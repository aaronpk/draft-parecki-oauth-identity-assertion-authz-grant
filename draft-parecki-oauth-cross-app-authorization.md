---
title: "OAuth Cross-Domain Authorization"
abbrev: "Cross-Domain Authz"
category: std

docname: draft-parecki-oauth-cross-domain-authorization
submissiontype: IETF
number:
date:
consensus: true
v: 3
area: AREA
workgroup: "Web Authorization Protocol"
keyword:
 - cross-domain
 - authorization
 - enterprise
venue:
  group: "Web Authorization Protocol"
  type: "Working Group"
  mail: "oauth@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/oauth/"
  github: "oktadev/draft-parecki-oauth-cross-domain-authorization"
  latest: "https://oktadev.github.io/draft-parecki-oauth-cross-domain-authorization/draft-parecki-oauth-cross-domain-authorization.html"

author:
 -
    fullname: Aaron Parecki
    organization: Okta
    email: aaron@parecki.com
 -
    fullname: Karl McGuinness
    organization: Okta
    email: public@karlmcguinness.com

normative:

informative:


--- abstract

TODO Abstract


--- middle

# Introduction

Enterprises often have hundreds of SaaS applications.  SaaS applications often have integrations to other SaaS applications that are critical to the application experience and jobs to be done.  When a SaaS app needs to request an access token on-behalf of a user to a 3rd party SaaS integration's API, the end-user needs to complete an interactive delegated OAuth 2.0 ceremony and consent.  The SaaS application is not in the same security or policy domain as the 3rd party SaaS integration.

It is industry best practice for an enterprise to connect their ecosystem of SaaS applications to their Identity Provider (IdP) to centralize identity and access management capabilites for the organization.  End-users get a better experience (SSO) and administrators get better security outcomes such multi-factor authentication and zero-trust.  SaaS applications today enable the administrator to establish trust with an IdP for user authentication but typically don't allow the administrator to trust the IdP for API authorization.  

The draft specification [Authorization Cross Domain Code 1.0](https://openid.bitbucket.io/draft-acdc-01.html) (ACDC) defines a new JWT-based grant type that can requested from an Authorization Server and exchanged with another Authorization Server for Access and Refresh tokens.  This new grant enables federation for Authorization Servers across policy or administrative boundaries. The same enterprise IdP for example that is trusted by applications for SSO can be extended to broker access to APIs.  This enables the enteprise to centralize more access decisions across their SaaS ecosystem and provides better end-user experience for users that need to connect multiple applications via OAuth 2.0.

This specification extends support for the Authorization Cross-Domain Code (ACDC) grant to [Token Exchange] (https://datatracker.ietf.org/doc/html/rfc8693) requests, enabling applications to request access to 3rd party applications using backchannel operations that don't interupt the end user's interactive application experience.  Its also useful for deployments where SSO is SAML based and not using OpenID Connect.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

## Roles

Requesting Application (Client)
: Application that wants to obtain an OAuth 2.0 access token on behalf of a signed-in user to an external/3rd party application's API that is managed by the same enterprise IdP.

Resource Application (Resource)
: Application that provides an OAuth 2.0 Protected Resource that is used across and enterprise's SaaS ecosystem.

Identity Provider (IdP)
: Organization's Identity Provider that is trusted by a set of applications in an enteprise's app ecosystem for identity and access management.



# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

TODO acknowledge.

