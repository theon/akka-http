<a id="authorizeasync"></a>
# authorizeAsync

## Signature

FIXME@@snip [SecurityDirectives.scala](../../../../../../../../../akka-http/src/main/scala/akka/http/scaladsl/server/directives/SecurityDirectives.scala) { #authorizeAsync }

## Description

Applies the given authorization check to the request.

The user-defined authorization check can either be supplied as a `=> Future[Boolean]` value which is calculated
just from information out of the lexical scope, or as a function `RequestContext => Future[Boolean]` which can also
take information from the request itself into account.

If the check returns `true` or the `Future` is failed the request is passed on to the inner route unchanged,
otherwise an `AuthorizationFailedRejection` is created, triggering a `403 Forbidden` response by default
(the same as in the case of an `AuthenticationFailedRejection`).

In a common use-case you would check if a user (e.g. supplied by any of the `authenticate*` family of directives,
e.g. @ref[authenticateBasic](authenticateBasic.md#authenticatebasic)) is allowed to access the inner routes, e.g. by checking if the user has the needed permissions.

See also @ref[authorize](authorize.md#authorize) for the synchronous version of this directive.

> **Note:**
See also @ref[Authentication vs. Authorization](index.md#authentication-vs-authorization-scala) to understand the differences between those.

## Example

@@snip [SecurityDirectivesExamplesSpec.scala](../../../../../../../test/scala/docs/http/scaladsl/server/directives/SecurityDirectivesExamplesSpec.scala) { #0authorizeAsync }