# Week 3 — Decentralized Authentication
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
