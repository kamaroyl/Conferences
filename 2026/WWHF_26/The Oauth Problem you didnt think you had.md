# The Oauth problem you didn't know you had
Speaker: Evier Tabora

Background
How Oauth is used
False trust
Abusing Oauth
demo


1970s Valet key --> Access to engine but not to car door or glove box

Derived keys (how to avoid using primary key for everything)
2007 Oauth 1.0
2009 Oauth 1.0a
2012 Oauth 2.0 (specification disagreements)
  Wide number of RFCs, kitchen sink approach
Misconceptions
- Not for authentication, for authorization
- MFA doesn't matter
- Application is vetted before going to the market place
  - But app is likely over permissioned
- Oauth servce to service, vpn doesn't matter
- Oauth consent phishing

Common attacks
- Consent Phishing
- Broad permissions
- Oauth permissions are persistant, need to revoke to remove

Taking advantage of Oauth
Google, Apple Microsoft are largest players
Ecosystems can be auth and resource 
Familiarity to uniform oatuh flow across all apps
OAUTH flows seem to have reduced scrutiny.
Microsoft and Google are great examples
  - Microsoft Power Atomate
  - Google Appscript

Using appscript
- Nothing to install (SAAS app)
- Javascript
- You can publish it
- Designed to integrate with _all_ of the google workspace

Whats the catch
  - Appscript forces Google review
  - Additional Oauth notifications
  - Timeouts and checks
No requirement for standardization of consent prompts

The workaround

- enterprise quirks of appscript
- public vs internal vs user oauth flow
- Systems calling oauth is handled differently by appscript
- Internal Use apps: only used by people in your google workspace
  - Your app will not be subject to the unverified app screen and the hundred user cap
  - context missing that the org is uncapped in size
  
1) Create a google sheet
2) embed app script
3) ensure access
4) deploy to entire org

Looks like oauth, no unverified markings, gives entire ecosystem access
Simplify via AI
  - Can generate in 10 minutes or less :horror:

Demo:

Generate script with AI 
Create sheeet with something that is interesting for a user
Add appscript
Name project (this shows up in consent prompt)
Deployed as web app
As user, whoever launches the web app and deploy to org

Defending against oauth attacks

- ubiquitous
- differentiatiing against malicious flows is hard

Identify apps
Only enabled needed apps
Prevent via automations

Identify all apps create a core baseline
  Allow list
Ticketing system automation to check for scopes, review

- Do not allow users to access any third party apps
  - Requires addition to allow list
- Disallow internal app
Can allow some with certain oauth scopes

