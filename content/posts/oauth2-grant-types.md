---
title: Oauth2 Grant Types 
date: 2018-07-18T10:25:15+07:00
draft: false
tags:
  - oauth2
---

OAuth2 provides several `grant types` for different use cases.

### Authorization Code Grant

![Authorization Code Grant]("/images/Authorization Code Grant.png")

### Implicit Grant

Previously, it was recommended that browser-based apps use the "Implicit" flow, which returns an access token immediately in the redirect and does not have a token exchange step. The industry best practice has changed to recommend that the authorization code flow be used without the client secret.

- https://tools.ietf.org/html/rfc8252#section-8.2
- https://oauth.net/2/pkce/

![Implicit Grant]("/images/Implicit Grant.png")

### Password Grant

![Password Grant]("/images/Password Grant.png")

### Client Credentials Grant
This grant is suitable for machine-to-machine authentication where a specific user’s permission to access data is not required.

![Client Credentials Grant]("/images/Client Credentials Grant.png")

### Refresh Token Grant

![Refresh Token Grant]("/images/Refresh Token Grant.png")
