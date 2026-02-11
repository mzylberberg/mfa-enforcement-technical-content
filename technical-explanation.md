# MFA Enforcement - Technical Explanation

## Overview
MFA enforcement requires users to complete a second authentication step during login. This reduces reliance on passwords alone and adds an extra layer of security from brute force attacks (e.g. dictionary attacks, password spraying, credential stuffing)

## Design Rationale
This MFA enforcement flow is designed to support risk-aware access decisions rather than one-size-fits-all authentication. Behavioral signals, such as keystroke dynamics, are used to reduce friction for low-risk login attempts, while OTP verification and escalation paths provide layered protection when risk thresholds are exceeded.

Escalation mechanisms and split-channel OTP delivery are included to preserve account security without defaulting to full lockout, supporting both security objectives and business continuity. Enrollment checks ensure policy compliance while maintaining a clear recovery path for legitimate users.

## Scope and Assumptions

This flow illustrates one example of a risk-adaptive MFA implementation. Not all MFA systems incorporate behavioral signals such as keystroke dynamics. In practice, organizations may rely on alternative contextual signals (e.g., device trust, location, time-of-day, or network posture) to inform authentication decisions.

The inclusion of behavioral authentication in this model is intended to demonstrate how adaptive signals can reduce unnecessary friction while preserving strong access controls, rather than to imply a universal MFA requirement.


## Authentication Flow (simplified)
1. User enters username + password
2. System validates credentials
3. Once MFA is required, system issues an MFA challenge
4. User approves/enters code
5. Access is granted (or denied if MFA fails)
6. If MFA fails, OTP can be a secondary option to verify authentication

> Diagram: `images/MFA%20Flow%20Diagram.pdf` (to be added)
> 
The authentication flow highlights key decision points where policy and risk thresholds influence access outcomes. Each branch represents an auditable control decision rather than an ad-hoc technical response, supporting transparency and consistent enforcement.


## Enrollment & Policy Behavior
- Users without MFA enrollment will be forced to enroll at next sign-in
- MFA methods allowed: (e.g., authenticator app, SMS, phone call,  hardware token)
- “Remember device” policy: (state whether allowed + duration, if applicable)

## Edge Cases & Controls
- Lost device / reset process
- Break-glass account handling (restricted, monitored)
- Service accounts (exemptions or alternate controls)
- Conditional access rules (location, device compliance, risk level)

## Validation Checklist
- [ ] MFA challenge triggered for all targeted users
- [ ] Enrollment flow works end-to-end
- [ ] Help desk runbook is available for common issues
- [ ] Monitoring/alerts in place for repeated MFA failures
