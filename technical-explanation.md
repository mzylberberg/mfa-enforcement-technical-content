# MFA Enforcement - Technical Explanation

## Overview
MFA enforcement requires users to complete a second authentication step during login. This reduces reliance on passwords alone.

## Authentication Flow (simplified)
1. User enters username + password
2. System validates credentials
3. If MFA is required, system issues an MFA challenge
4. User approves/enters code
5. Access is granted (or denied if MFA fails)

> Diagram: `images/mfa-flow.png` (to be added)

## Enrollment & Policy Behavior
- Users without MFA enrollment will be forced to enroll at next sign-in
- MFA methods allowed: (list your assumed options, e.g., authenticator app, SMS, hardware token)
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
