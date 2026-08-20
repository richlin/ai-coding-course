---
title: Debugging Loop
tags: [type/concept]
related: [[Small Reversible Increments]], [[Test-Driven Development Cycle]], [[Verification Hierarchy]]
---

# Debugging Loop

A five-step evidence chain for fixing a failure: **reproduce, localize, explain, fix, guard.** Recovery — returning to a known-good state after a wrong edit or invalid assumption — is the companion move when a speculative fix makes things worse instead of better.

## The five steps

| Step | Question it answers |
|---|---|
| Reproduce | What is the smallest input/command that reliably triggers the failure? |
| Localize | Which specific boundary or function is responsible — tested directly, bypassing unrelated layers? |
| Explain | Why does the existing code produce this output — what mechanism, not just what symptom? |
| Fix | What is the smallest change that addresses the explained cause? |
| Guard | What regression test, using realistic inputs, prevents recurrence? |

## Why evidence beats guessing

Agents can generate several plausible fixes quickly without ever identifying the root cause. Evidence narrows the space of causes; guesses only add more candidate explanations. A reproducible failure is a stable target for both diagnosis and verification — the same reproduction used to find the bug is the one rerun to confirm the fix.

## Root cause vs. trigger vs. symptom

These are distinct and easy to conflate: CSV quoting (existing behavior) protects commas and quotes, but does not prevent spreadsheet formula interpretation (a different mechanism) — the symptom (bad export) and the trigger (a `=`-prefixed value) point at a boundary that the current fix doesn't actually cover. Explaining *why* a fix addresses the observed cause is what distinguishes a fix from a coincidence.

## Recovery discipline

Change one variable at a time. Do not stack speculative fixes until the symptom disappears — that produces code nobody can explain later. Return to a known-good checkpoint after a speculative edit fails rather than layering another edit on top of unverified state. Do not declare recovery until the original reproduction and the new regression guard both pass.

Source: [[Debugging and Recovery - AI Coding Course]]
