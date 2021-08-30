---
title: Azure Active Directory integrations with authentication 
date: 2021-08-30T12:36:20+05:30
author: Praveen Parashar
categories: [Azure]
tags: [Azure, Advance-concepts, Authentication, AzureAD,interview]
description: Azure Active Directory integrations with authentication
---  

### The following table presents authentication Azure AD integration with legacy authentication protocols and their capabilities ###

  <a href="Reference https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/auth-sync-overview"> reference </a>

#### OAuth 2.0 authentication with Azure Active Directory

he OAuth 2.0 is the industry protocol for authorization. It allows a user to grant limited access to its protected resources. Designed to work specifically with Hypertext Transfer Protocol (HTTP), OAuth separates the role of the client from the resource owner. The client requests access to the resources controlled by the resource owner and hosted by the resource server. The resource server issues access tokens with the approval of the resource owner. The client uses the access tokens to access the protected resources hosted by the resource server.

OAuth 2.0 is directly related to OpenID Connect (OIDC). Since OIDC is an authentication and authorization layer built on top of OAuth 2.0, it isn't backwards compatible with OAuth 1.0. Azure Active Directory (Azure AD) supports all OAuth 2.0 flows.

<image src="https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/media/authentication-patterns/oauth.png" />

#### Components of system

User: Requests a service from the web application (app). The user is typically the resource owner who owns the data and has the power to allow clients to access the data or resource.

Web browser: The web browser that the user interacts with is the OAuth client.

Web app: The web app, or resource server, is where the resource or data resides. It trusts the authorization server to securely authenticate and authorize the OAuth client.

Azure AD: Azure AD is the authorization server, also known as the Identity Provider (IdP). It securely handles anything to do with the user's information, their access, and the trust relationship. It's responsible for issuing the tokens that grant and revoke access to resources.


#### OpenID Connect authentication with Azure Active Directory

OpenID Connect (OIDC) is an authentication protocol based on the OAuth2 protocol (which is used for authorization). OIDC uses the standardized message flows from OAuth2 to provide identity services.

The design goal of OIDC is "making simple things simple and complicated things possible". OIDC lets developers authenticate their users across websites and apps without having to own and manage password files. This provides the app builder with a secure way to verify the identity of the person currently using the browser or native app that is connected to the application.

The authentication of the user must take place at an identity provider where the user's session or credentials will be checked. To do that, you need a trusted agent. Native apps usually launch the system browser for that purpose. Embedded views are considered not trusted since there's nothing to prevent the app from snooping on the user password.

In addition to authentication, the user can be asked for consent. Consent is the user's explicit permission to allow an application to access protected resources. Consent is different from authentication because consent only needs to be provided once for a resource. Consent remains valid until the user or admin manually revokes the grant.

### Use When 
here is a need for user consent and for web sign in.

<image  src ="https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/media/authentication-patterns/oidc-auth.png" />


 #### Components of system

User: Requests a service from the application.

Trusted agent: The component that the user interacts with. This trusted agent is usually a web browser.

Application: The application, or Resource Server, is where the resource or data resides. It trusts the identity provider to securely authenticate and authorize the trusted agent.

Azure AD: The OIDC provider, also known as the identity provider, securely manages anything to do with the user's information, their access, and the trust relationships between parties in a flow. It authenticates the identity of the user, grants and revokes access to resources, and issues tokens.

#### Microsoft identity platform and OpenID Connect protocol

OpenID Connect (OIDC) is an authentication protocol built on OAuth 2.0 that you can use to securely sign in a user to an application. When you use the Microsoft identity platform's implementation of OpenID Connect, you can add sign-in and API access to your apps. This article shows how to do this independent of language and describes how to send and receive HTTP messages without using any Microsoft open-source libraries.

OpenID Connect extends the OAuth 2.0 authorization protocol for use as an authentication protocol, so that you can do single sign-on using OAuth. OpenID Connect introduces the concept of an ID token, which is a security token that allows the client to verify the identity of the user. The ID token also gets basic profile information about the user. It also introduces the UserInfo endpoint, an API that returns information about the user.

### The most basic sign-in flow has the steps shown in the next diagram. Each step is described in detail in this article.

 <image src= "https://docs.microsoft.com/en-us/azure/active-directory/develop/media/v2-protocols-oidc/convergence-scenarios-webapp.svg" />

 for more Reference
 <a href="https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-protocols-oidc">reference </a>

### Permissions and consent in the Microsoft identity platform
 Reference <a href="https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-permissions-and-consent">reference </a>


### Microsoft identity platform ID tokens

 <a href="https://docs.microsoft.com/en-us/azure/active-directory/develop/id-tokens#validating-an-id-token">reference </a>

### Microsoft identity platform UserInfo endpoint
 reference <a href="https://docs.microsoft.com/en-us/azure/active-directory/develop/userinfo" >reference </a>





