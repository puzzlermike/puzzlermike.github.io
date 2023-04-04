---
title: "OAuth 2.0 Best Practice - Grant Types"
date: 2023-03-26T09:07:31+02:00
draft: false
---

# Intro

The official OAuth 2.0 specification defines several grant types:

- Authorization Code
- Implicit
- Resource Owner Password Credentials
- Client Credentials

In this blog post we will summarize the intended usage of each grant type, their communication flow and the current best practices.

# Authorization Code Grant Type

The authorization code grant type is a redirection-based grant type.<br />
This means that the user interacts with the authorization server using a user-agent (typically a web browser).<br />
After a successful authorization request, the user-agent receives an `authorization code` from the authorization server.<br />
The client exchanges the received authorization code for an `access token` which can be used to make authorized API calls against the resource server.

## Authorization Endpoint

The client application redirects the user to the authorization server using a user-agent to initiate authorization code flow.<br />
The redirection target is the `authorization` endpoint that specifies the following query parameters:

- response_type - Indicates what the authorization server returns to the user after a successful authorization request
- client_id - A string that identifies the client application
- redirect_uri - This is where the user is redirected to after the authorization request
- scope - Defines the scope that the client application requests, for example `profile`
- state - The state paramter is used to prevent CSRF (Cross-Site-Request-Forgery) attacks

The state parameter is covered in detail in another blog post.

## Token Endpoint