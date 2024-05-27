
# creators 

https://bendingspoons.com/products



# HACKERONE PAGE 
https://hackerone.com/evernote?type=team

# WHAT IS IT 
Evernote is a popular note-taking application that allows users to capture, organize, and share notes across various devices. It's known for its versatility, enabling users to create text notes, checklists, voice memos, and even attach files like images and PDFs.




# api reference
 https://dev.evernote.com/doc/reference/
# sdk javascript
 https://github.com/evernote/evernote-sdk-js


# Attach surface 

![[scopes_for_evernote_at_2024-05-01_13_41_30_UTC.csv]]

| **elegible for money**<br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **accounts.evernote.com** <br><br>CouchbaseJava                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| **api.evernote.com**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| <br>is the API gateway into Evernote's microservice infrastructure. The microservice infrastructure is managed by Istio and is provisioned by Google Kubernetes Engine (GKE). Traffic is HTTP or gRPC, depending on the service being interacted with.<br><br><br>Docker Express google cloud java javaScript Kubernetes node.js typescript<br><br>                                                                                                                                                                                                                                                 |
| **www.evernote.com**<br><br>[www.evernote.com](http://www.evernote.com/) serves the main Evernote web app. It also exposes several HTTP and Thrift endpoints that the Evernote mobile/desktop apps use to communicate with the service. Almost all endpoints on the www. domain are routed by HAProxy to an array of Java based Tomcat/Struts shards.<br><br><br>**non elegible for money but useful**<br>                                                                                                                                                                                          |
| **[[accounts.stage.evernote.com]]** <br><br>This is the staging environment for accounts.evernote.com; vulnerabilities found here will not be eligible for bounty unless the vulnerability is also present in production.<br>                                                                                                                                                                                  \|<br>\| **api.stage.evernote.com**<br><br><br>This is the staging environment for api.evernote.com; vulnerabilities found in this staging environment are not eligible for bounty * |
| **api.stage.evernote.com**<br><br><br>This is the staging environment for api.evernote.com; vulnerabilities found in this staging environment are not eligible for bounty *unless the vulnerability is verified in the corresponding production environments*.                                                                                                                                                                                                                                                                                                                                      |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |


# Test Plan

- [www.evernote.com](http://www.evernote.com/) (excluding evernote.com) [https://www.evernote.com/Login.action](https://www.evernote.com/Login.action) is the major access point for our customers to use our service through web browsers. This domain also provides the backend APIs for our desktop and mobile clients.

- Feel free to create test accounts using your [@wearehackerone](https://hackerone.com/wearehackerone) alias. Please conduct your testing mainly on our production server as we have protection, such as rate limiting, enabled on production.

- stage.evernote.com is the corresponding staging environment. For any accounts that may require payment information, this staging environment allows use of test credit card numbers: [https://docs.adyen.com/development-resources/test-cards/test-card-numbers](https://docs.adyen.com/development-resources/test-cards/test-card-numbers)
# Out of scope vulnerabilities

### When reporting vulnerabilities, please consider (1) attack scenario / exploitability, and (2) security impact of the bug. The following issues are considered out of scope:

- Clickjacking on pages with no sensitive actions.
- Password, email and account policies, such as email id verification, reset link expiration, password complexity.
- Cross-Site Request Forgery (CSRF) on unauthenticated forms or forms with no sensitive actions.
- Self-XSS and issues exploitable only through Self-XSS.
- Attacks requiring MITM or physical access to a user's device.
- Previously known vulnerable libraries without a working Proof of Concept.
- Comma Separated Values (CSV) injection without demonstrating a vulnerability.
- Missing best practices in SSL/TLS configuration.
- Any activity that could lead to the disruption of our service (DoS).
- Content spoofing and text injection issues without showing an attack vector/without being able to modify HTML/CSS.
- Hosting malware/arbitrary content on Evernote and causing downloads.
- Rate limiting or bruteforce issues on non-authentication endpoints.
- Reports from automated tools or scans.
- Reports of spam (i.e., any report involving ability to send emails without rate limits).
- Login/Forgot Password page account bruteforce or account lockout not enforced.
- Missing best practices in Content Security Policy or best practice security headers (Including Cross-Origin Resource and Host header issues).
- Missing HttpOnly or Secure flags on cookies.
- Presence of autocomplete attribute on web forms.
- Any report that discusses how you can learn whether a given username, email address has a Evernote account.
- Any access to data where the targeted user needs to be operating a rooted mobile device.
- Any report on bypassing our storage limits etc. is out of scope.
- Any report about DLL hijacking without demonstrating how it gains new privileges is also out of scope.
- Absence of rate limiting, unless related to authentication.
- IP/Port Scanning via Evernote services unless you are able to hit private IPs or Evernote servers.
- Devices (ios, android, desktop apps) not getting unlinked on password or 2FA change.
- Missing email best practices (Invalid, incomplete or missing SPF/DKIM/DMARC records, etc.).
- Vulnerabilities only affecting users of outdated or unpatched browsers [Less than 2 stable versions behind the latest released stable version].
- Software version disclosure / Banner identification issues / Descriptive error messages or headers (e.g. stack traces, application or server errors, HTTP 404 codes/pages or other HTTP non-200 codes/pages).
- Public Zero-day vulnerabilities that have had an official patch for less than 1 month will be awarded on a case by case basis.
- Tabnabbing.
- Open redirect - unless an additional security impact can be demonstrated.
- Issues that require unlikely user interaction.
- Third party hosted services.
- Vulnerabilities that allow for users to use our products and services for free or for a cheaper price.
- Broken links to external domains in our blog and marketing pages.
- Reports that solely contain a list of compromised email, password pairs belonging to users without demonstrating the exploit used to obtain that list.

# terms 
- **All automated scanning must include your H1 username in the `user agent` in order to be eligible for bounty**.

- **All authenticated testing must be performed using [@wearehackerone](https://hackerone.com/wearehackerone) aliases**.

- Please provide detailed reports with reproducible steps. If the report is not detailed enough to reproduce the issue, the issue will not be eligible for a reward.

- Submit one vulnerability per-report, unless you need to chain vulnerabilities to provide impact.

- When duplicates occur, we only award the first report that was received (provided that it can be fully reproduced).

- **Multiple vulnerabilities caused by one underlying issue** will be awarded one bounty.

- **Social engineering (e.g. phishing, vishing, smishing) is prohibited**.

- **Network Level DDoS/DoS attacks are forbidden**. Application volumetric DDoS/DoS attacks are forbidden. To prevent being locked out, please throttle automated testing.

 - **Avoid privacy violations**, destruction of data, and interruption or degradation of our service. Only interact with accounts you own, or with accounts for which you have the express written permission of the account holder.

- **You must not be a current or a former employee of Evernote or its subsidiaries** or related entities.

- You agree to cooperate with Evernote, including by answering any questions we may ask you in a timely manner and in good faith.




