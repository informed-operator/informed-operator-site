---
layout: post
title: "Algorithmic Hiring and Title VII: Applying Griggs v. Duke Power to AI"
date: 2025-08-18
tag: policy
excerpt: "The disparate impact framework established in 1971 may be the most powerful existing tool for regulating AI-driven employment decisions. Here's why, and what its limits are."
---

When companies began automating hiring decisions with machine learning models, the legal framework most relevant to regulating them was already fifty years old. *Griggs v. Duke Power Co.* (1971) established that employment practices with a disparate impact on protected groups are unlawful under Title VII — even without discriminatory intent. The question is whether that framework translates cleanly to algorithmic systems.

## The Griggs Framework

The holding in *Griggs* was straightforward: Duke Power required a high school diploma and an IQ test score for certain positions. Black applicants failed at higher rates than white applicants. The Court held that Title VII prohibits "not only overt discrimination but also practices that are fair in form, but discriminatory in operation."

The burden-shifting structure that followed: a plaintiff establishes disparate impact through statistical evidence; the burden shifts to the employer to show the practice is job-related and consistent with business necessity; if the employer meets that burden, the plaintiff can still prevail by showing a less discriminatory alternative exists.

## The Translation Problem

Applying this to algorithmic hiring creates several complications.

**Auditability.** Disparate impact analysis requires knowing the selection rates for different demographic groups. Many algorithmic systems produce scores or rankings without exposing the features driving them. A plaintiff establishing impact needs data the employer may claim it doesn't retain.

**Proxies.** A model trained on historical hiring data may learn to use zip codes, school names, or employment gaps as proxies for protected characteristics — without the protected characteristic ever appearing as an input feature. The discriminatory pattern is real; the mechanism is invisible.

**Business necessity.** Courts have generally deferred to employer judgment on what constitutes a valid predictor of job performance. Whether that deference survives when the employer's evidence is "the model said so" is unresolved.

## Where This Is Headed

The EEOC has issued guidance making clear it views automated systems as subject to existing anti-discrimination law. The question of how courts will handle proxy discrimination claims — particularly in models where features interact in ways even the developers don't fully understand — will define the practical limits of Title VII in the algorithmic hiring context.

The Griggs framework is genuinely powerful here. Disparate impact liability doesn't require proving intent. In a domain where discriminatory outcomes can emerge from training data without any discriminatory design decision, that matters.

---

*This analysis draws on research conducted for the Law and Technology Policy seminar at the University of Pittsburgh.*
