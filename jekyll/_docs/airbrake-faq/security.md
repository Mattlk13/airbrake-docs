---
layout: classic-docs
title: Security
categories: [airbrake-faq]
description: Airbrake Security and Compliance
---

### Is data encrypted in transit?
Communication between customers and Airbrake is by default sent securely
via TLS.

Airbrake currently supports TLS protocol v1.2.

Support for TLSv1.0 and TLSv1.1 was deprecated on June 30, 2018.

## Is data encrypted at rest?
All Airbrake customer data is stored encrypted at rest. This includes backups.

## Where is Airbrake hosted?
Airbrake is hosted on Amazon Web Services in facilities which maintain
various levels of compliance, certifications and assurance. More information
can be found on the [AWS security pages](https://aws.amazon.com/security/) or [requested from AWS](https://pages.awscloud.com/compliance-contact-us.html).

## Does Airbrake have two-factor authentication?
Two-factor authentication is available for all paid plans and can be enabled on
your [profile page](https://airbrake.io/users/edit). For more info on how to set
up the two-factor authentication, please visit the
[two-factor authentication doc](/docs/features/two-factor-authentication).

Airbrake also supports the two-factor authentication as part of the GitHub
single sign-on feature. By enabling the two-factor authentication on your GitHub
profile you help secure your Airbrake account with an extra layer of security.

## Does Airbrake maintain any certifications, attestation, or compliance?
Airbrake has [certified it's compliance](https://www.privacyshield.gov/participant?id=a2zt0000000TTiJAAW) with the EU-U.S. and Swiss-U.S [Privacy Shield](https://www.privacyshield.gov) as set forth by the U.S. Department of commerce.

Airbrake also maintains GDPR compliance. For our EU customers we offer a Data Protection Addendum available by contacting <a href="mailto:privacy@airbrake.io?subject=GDPR Data Protection Addendum">privacy@airbrake.io</a>.

To fulfill our part of the [shared responsibility model](https://aws.amazon.com/compliance/shared-responsibility-model/) for cloud services Airbrake has completed a [SOC 2 Type 2 Audit](https://www.aicpa.org/interestareas/frc/assuranceadvisoryservices/aicpasoc2report.html) audit under the Security Trust Principle.

## What about PCI DSS?
Airbrake's payment and card information is handled by [Stripe](https://stripe.com/docs/security) a certified [PCI Level 1 Service Provider](http://www.visa.com/splisting/searchGrsp.do?companyNameCriteria=stripe,%20inc). Stripe has been audited by an independent PCI Qualified Security Assessor (QSA) and is certified PCI DSS compliant.

When accepting payments Airbrake does so in a PCI compliant manner. Our PCI SAQ is available by <a href="mailto:support@airbrake.io?subject=PCI SAQ">contacting support<a/>.

## Vulnerability or security disclosure

If you would like to report a vulnerability, security issue or have other security related concerns about an Airbrake product please contact <a href="mailto:security@airbrake.io">security@airbrake.io</a>.

If you are disclosing a vulnerability please do so [responsibly](https://en.wikipedia.org/wiki/Responsible_disclosure) and provide

- a summary of the vulnerability
- a proof of concept
- a list of tools used
- the output from the tools used
- the commands used to execute the tools

Please note Airbrake **DOES NOT** maintain a bug bounty program. Airbrake also **DOES NOT** pay for unsolicited disclosures.
