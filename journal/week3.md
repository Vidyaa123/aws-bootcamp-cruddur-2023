# Week 3 — Decentralized Authentication

### [Setup Cognito User Pool](setup-cognito-user-pool)
### [Implement SignIn & SignUp Page](implement-signin-&-signup-page)
### [Implement Custom Confirmation & Regcovery Page](implement-custom-confirmation-&-recovery-page)
### [Different approaches to verifying JWTs](different-approaches-to-verifying-jwts)
### [Amazon Cognito Security Best Practices](amazon-cognito-security-best-practices)
### Amazon Cognito Security Best Practices
### Setup Cognito User Pool
Provision and setup AWS Cognito via Click-Ops. Needs a valid AWS Account.
##### ![Screenshot](Screenshot2023-03-08-01.png)

### Amazon Cognito Security Best Practices
#### Client side Applications
  - Traditional Authentication (Credentials)
      - username & password
      - physical access card

  - Single Sign ON/SAML (Security Assertion markup Language)
  - OAuth
  - OpenID - social credentials to authenticate (dont nedd to create a new account), Only Authentication no Authorization
  - Authorisation will be provided by OAuth2.0
  - OpenID & OAuth together
 
 #### Decentralized Authentication
  - Store username & password in one location and authorize all applications from this one location
  - dont need to use different username and password between different applications
  -
 #### Amazon Cognito
  - user directory with context of amazon services
  - UserPools (Add user directories to your app)
      - Cognito User pools
      - Federated Identities
  - IdentityPools (Grant access to AWS Services)

#### User Lifecycle Management
  - user identity
  - New employee - Provision (Azure directrory, Amazon direcrtory) - Enforced policies - Update policies - Offboard 
  - Regularly update and review user policies

#### Token Lifecycle Management
