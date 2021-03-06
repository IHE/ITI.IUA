# IUA work item

Improve IUA based on lessons-learned

Working group rendering https://ihe.github.io/ITI.IUA/IHE_ITI_Suppl_IUA

Comments can be submitted https://github.com/IHE/ITI.IUA/issues/new?assignees=&labels=&template=public-comment-issue-template.md&title=

using kanban board for managing tasks https://github.com/IHE/ITI.IUA/projects/1

## Breaking changes

* Replacement of the "Bearer" option with "Token Introspection" option. This option utilizes OAuth2 Introspect (RFC 7662). This option allows Resources Servers to deal with any token format (JWT/SAML/other) by obtaining the claims associated with an access token through an introspect API offered by the Authorization Server.

* Removal of hard requirement for JWT formatted access token support. JWT, SAML and Introspect have all become optional. Resource and Authorization Servers need to implement at least one.

* The IHE-JWT and IHE-SAML HTTP Authorization schemes have been replaced by the "Bearer" scheme to be compatible with RFC 6750. All token formats are now treated as bearer tokens. The Authorization Client does no longer need to be aware of the token format.

* The "audience" claim associated to an access token can now be a JSON array of server identifiers. Resource Servers still MUST check their presence in the audience claim.

* Custom claim names have been replaced by established JWT (Access Token) RFC claims whenever possible and aligned with the UDAP extensions mechanism.

## Open questions

* The addendum contains a section on IHE-MHD to indicate authorization scope specification and usage. MHD is used as example case, extendable to other profiles that employ RESTful APIs. Open question is how the profile specific authorization scopes should be specified, and if, when an how they should relate to HEART/SmartOnFHIR scopes.

## Other changes

* Reworked the Use Cases section and added descriptions of the use cases from the user perspective.

* Reworked the text descriptions to establish the borders between authentication, authorization and policy enforcement.

* Incorporated the Change Proposals on IUA

* Aligned with the new OAuth 2.1 draft specification.

* Cleaned up and updated references to OAuth related RFC's.

* Established authorization code and client credential flow to the Get Authorization Token options.

* Added support for OAuth public clients.

* Established UDAP extensions to improve the structure of JWT and reworked the examples.

* Aligned the profile with the latest standards such as OAuth 2.1, OpenId Connect, JWT, OAuth2 Introspect.

* Resource field in token request has become optional for client, should be supported by authorization server.

* Removal of references to FHIR/Heart scopes. IUA is now scope definition agnostic. Scopes to be added to REST/FHIR based IHE profiles.

* Introduction of option for OAuth2 Authorization Server Metadata (RFC8414). The metadata document contains references to endpoint locations, signing key material, and an indication of the issued token format.

* Updates to support service-to-service authorization schemes (eg., by removing strong dependencies on user consent).

* Improved profiling of OAuth2 interactions providing clarity on request/response data requirements and semantics.

* Support for alternative authorization grants (e.g. client jwt_grants). Not mandatory to be supported by an Authorization Server

* Added an option to ATNA that leverages IUA with server side https

