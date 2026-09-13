---
layout: post
title: "The Benefits of GRC Engineering"
#excerpt: "What was the nature of Google's relationship with Character.AI - typical service provider or low key partner?"
#category: "Policy Research"
tags: [GRC Engineering]
tag: grc
featured: true
---

Compliance audits have long consisted of screenshots, among other artifacts, as proof that a certain control is in place. While this is useful in the moment, it does not guarantee that in even the short-term that this control will be intact, especially given the many changes happening in a production environment. Think about it - if a system receives hundreds of code and configuration changes per day, and those changes are continuously integrated, how can anyone be certain that none of those changes wiped out the efficacy of these controls? If code is going to be continuously integrated and deployed, the compliance checks need to ride shotgun and be automated in the deployment gate.

I've worked on code bases which had continuous integration and deployment. These integrations often feature steps such as linting - which found less than optimal code syntax and suggested improvements - along with testing - both unit (which focuses on specific pieces of code) and integration (focuses on the outcomes of the interplay of code). This is also a place where compliance can be proven automatically; this is known as Policy as Code. One example is Infrastructure as Code checking, which can ensure that any computing resources obtained by platforms such as Terraform jibe with identity and access management controls that would minimize the effects of a user's credentials being compromised. If a developer commits a Terraform script that opens a bucket publicly or violates an IAM baseline, the build pipeline fails, notifications go out via Slack, and the issue is corrected before code ever hits production.

Security has been perceived as an afterthought in some product development lifecycles. This is the antidote - the CI/CD pipeline is revealing pitfalls during every build, preventing products from giving them enough rope to hang themselves on an audit, or even a breach. Embedding automated checks into CI/CD turns compliance from a slow annual audit panic into a continuous, real-time feedback loop.