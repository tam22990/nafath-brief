Version: NAFATH-V1
Track: Software

Overview

A national single sign-on service must let citizens access multiple government websites and mobile apps through one account. Its software needs clear identity and access controls, while AI may help identify suspicious login patterns but must be tested for errors and unfair outcomes. The mobile app should request only necessary permissions and explain their purpose. Network protections such as DNS over HTTPS can reduce exposure of DNS queries, but they do not hide all user activity. Cybersecurity controls must resist phishing, protect accounts, and limit the impact of compromised services. Because the platform handles sensitive identity data, the authority must apply Oman’s data-protection requirements, restrict access, and protect stored records. A key software decision is using OpenID Connect for user sign-in and OAuth 2.0 for delegated access to protected resources.

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

DNS over HTTPS (DoH) sends DNS queries through encrypted HTTPS connections. It helps prevent other parties on the network from reading or modifying DNS traffic while it is in transit. However, DoH does not hide the user’s IP address, encrypt all application traffic, or prevent a website from tracking the user. The authority should assess its chosen DNS provider, logging practices, and privacy policy before deploying DoH for the login service.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484

Cybersecurity

Phishing-resistant authentication prevents a stolen password or code from being enough to impersonate a user on a fake website. FIDO2/WebAuthn security keys and platform authenticators provide this protection by binding authentication to the legitimate service. SMS codes, email codes, and ordinary one-time passwords can still be stolen through phishing. Push approval with number matching improves protection against approval fatigue but is not fully phishing-resistant. The authority should prioritize FIDO/WebAuthn for high-risk accounts.

Resource: Implementing Phishing-Resistant MFA - https://www.cisa.gov/sites/default/files/2023-01/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf

Data

Oman’s Personal Data Protection Law requires organisations handling personal data to meet applicable legal duties, including obtaining consent where required and respecting data subjects’ rights. For the login service, the authority should explain why identity data is collected, limit collection to legitimate needs, restrict access, and protect stored records against unauthorised use. It must also follow applicable rules for data-subject requests and personal-data breaches. The authority should verify its specific duties against the law and executive regulation before launch.

Resource: Royal Decree 6/2022 - Promulgating the Personal Data Protection Law - https://www.mtc.gov.om/itaportal/Data/English/DocLibrary/2024115132533256/PROMULGATING%20THE%20PERSONAL%20DATA%20PROTECTION%20LAW.pdf

Misconception in My Track

A common misconception is that OAuth 2.0 is itself a login protocol. The OAuth 2.0 specification focuses on delegated access to protected resources through access tokens; it does not define a standard way to report that a user has authenticated. OpenID Connect adds that identity layer and defines an ID Token containing authentication claims. This distinction matters because an API access token and an identity token serve different purposes and must be validated for their intended use. See Section 1.1, “Introduction,” of the OpenID Connect Core 1.0 specification.

Open Question

How should the authority validate tokens across different government services while preventing one compromised service from exposing citizens’ identities or granting unauthorised access to other services?
