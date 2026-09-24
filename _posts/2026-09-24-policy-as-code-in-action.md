---
layout: post
title: "Policy as Code in Action"
excerpt: "A concrete example of policy as code"
#category: "Policy Research"
tags: [GRC Engineering]
tag: grc
featured: true
---

In the previous article, I explored the motivations for taking an engineering approach to GRC. Here, I’ll look at how to implement this in practice: Policy-as-Code.

A recurring goal in modern engineering teams is to "shift left"—moving critical activities like security validation earlier (from right to left) in the software development lifecycle (SDLC). Finding misconfigurations early makes remediation simpler and drastically cheaper. As code progresses toward production, problematic modules spread across more dependencies, making regression testing and surgical fixes far harder. From a GRC perspective, shifting left transforms compliance from a delayed, sample-based audit into a real-time deployment gate.

To catch violations as early as possible, a policy engine like Open Policy Agent (OPA) evaluates application code or infrastructure definitions (such as Terraform plan JSON) directly within a CI/CD pipeline. The checks become automatic—a failed build due to a policy violation becomes the squeaky wheel that gets immediate attention.

**A Rego Example for an AWS S3 Bucket**

Consider a scenario where a JSON file representing an S3 bucket configuration is evaluated by a Rego policy file (s3_public_access.rego).

To pass evaluation, the bucket configuration must **not**:

1.  Have an Access Control List (ACL) set to "public-read".

2.  Have an ACL set to "public-read-write".

3.  Contain policy statements with Effect: "Allow" and a public Principal: "*".

For every violation detected, an error message is appended to the deny set. The configuration passes only if deny is empty.


```
package s3.security

# Input is expected to be a JSON representation of an S3 bucket configuration
# Example: Terraform plan JSON or AWS API output

default allow = false

# Deny if bucket ACL is public
deny[msg] {
    input.acl == "public-read"
    msg := sprintf("Bucket '%s' has public-read ACL", [input.name])
}

deny[msg] {
    input.acl == "public-read-write"
    msg := sprintf("Bucket '%s' has public-read-write ACL", [input.name])
}

# Deny if bucket policy allows access to everyone
deny[msg] {
    some statement
    statement := input.policy.Statement[_]
    statement.Effect == "Allow"
    statement.Principal == "*"
    msg := sprintf("Bucket '%s' policy allows public access", [input.name])
}

# Allow only if no deny rules match
allow {
    not deny[_]
}
```
If the below JSON file, `bucket.json`, is evaluated with the above Rego policy file...

```json
{
  "name": "my-bucket",
  "acl": "public-read",
  "policy": {
    "Statement": [
      {
        "Effect": "Allow",
        "Principal": "*",
        "Action": "s3:GetObject",
        "Resource": "arn:aws:s3:::my-bucket/*"
      }
    ]
  }
}
```

using this command on the OPA CLI...
```bash
opa eval --data s3_public_access.rego --input bucket.json "data.s3.security.deny"
```


The output will be:
```json
[
  "Bucket 'my-bucket' has public-read ACL",
  "Bucket 'my-bucket' policy allows public access"
]
```

Integrated into a CI/CD pipeline step, this non-empty `deny` result triggers a build failure. Developers receive immediate feedback on exact policy breaches—enabling them to restrict the ACL and policy statements before any non-compliant infrastructure is provisioned.