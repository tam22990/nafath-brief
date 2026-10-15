Version: NAFATH-V1
Track: Software

Overview

A national digital login service must let citizens access many government websites and mobile apps through one account. The system needs reliable software standards so services can confirm who a user is and control what that user may access. Artificial intelligence may help identify unusual login attempts, but its decisions must be tested for accuracy, bias, privacy, and human oversight. The mobile app should request only necessary permissions and explain why they are needed. Networking protections can reduce exposure of DNS lookups, while cybersecurity controls must defend users against phishing and account theft. Because the service handles sensitive citizen information, the authority must follow data-protection duties, limit access, and protect stored data. These areas must work together so login is usable, secure, and trustworthy.

Software

OAuth 2.0 and OpenID Connect solve different problems. OAuth 2.0 lets an application access protected resources using access tokens, but it does not define a standard way to authenticate the end user. OpenID Connect adds an identity layer and uses an ID Token to communicate authentication information. For a national login service, OpenID Connect should handle sign-in, while OAuth 2.0 should support delegated API access. An access token should not be treated as proof of identity.

Resource: OpenID Connect Core 1.0 - https://openid.net/specs/openid-connect-core-1_0.html

AI

Before an AI model flags suspicious logins, the authority should apply the NIST AI Risk Management Framework. It should test accuracy and reliability, measure false alerts and missed attacks, and check whether results unfairly affect particular user groups. Login data must be protected, and access to the model must be secured. The authority should document how alerts are used, assign responsibility for decisions, monitor performance after deployment, and provide human review before serious actions such as account suspension.

Resource: AI Risks and Trustworthiness - https://airc.nist.gov/airmf-resources/airmf/3-sec-characteristics/

Mobile

Android runtime permissions limit an app’s access to certain sensitive data and device features. The app must declare relevant permissions, check whether access has already been granted, and request permission when a protected feature is needed. Users can deny requests, so the app must handle denial safely rather than assume access. A government login app should avoid unnecessary permissions, explain why sensitive access is needed, and keep core sign-in functions working when optional permissions are refused.

Resource: Google Play services and runtime permissions - https://developers.google.com/android/guides/permissions

Networking

Cybersecurity

Data

Misconception in My Track

Open Question
