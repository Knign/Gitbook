# Server Side

## SQL injection

* [SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](sql-injection/sql-injection-vulnerability-in-where-clause-allowing-retrieval-of-hidden-data.md)
* [SQL injection vulnerability allowing login bypass](sql-injection/sql-injection-vulnerability-allowing-login-bypass.md)
* [SQL injection attack, querying the database type and version on Oracle](sql-injection/sql-injection-attack-querying-the-database-type-and-version-on-oracle.md)
* [SQL injection attack, querying the database type and version on MySQL and Microsoft](sql-injection/sql-injection-attack-querying-the-database-type-and-version-on-mysql-and-microsoft.md)
* [SQL injection attack, listing the database contents on non-Oracle databases](sql-injection/sql-injection-attack-listing-the-database-contents-on-non-oracle-databases.md)
* [SQL injection attack, listing the database contents on Oracle](sql-injection/sql-injection-attack-listing-the-database-contents-on-oracle.md)
* [SQL injection UNION attack, determining the number of columns returned by the query](sql-injection/sql-injection-union-attack-determining-the-number-of-columns-returned-by-the-query.md)
* [SQL injection UNION attack, finding a column containing text](sql-injection/sql-injection-union-attack-finding-a-column-containing-text.md)
* [SQL injection UNION attack, retrieving data from other tables](sql-injection/sql-injection-union-attack-retrieving-data-from-other-tables.md)
* [SQL injection UNION attack, retrieving multiple values in a single column](sql-injection/sql-injection-union-attack-retrieving-multiple-values-in-a-single-column.md)

## Business logic vulnerabilities

* [Excessive trust in client-side controls](business-logic-vulnerabilities/excessive-trust-in-client-side-controls.md)
* [High-level logic vulnerability](business-logic-vulnerabilities/high-level-logic-vulnerability.md)
* [Inconsistent security controls](business-logic-vulnerabilities/inconsistent-security-controls.md)
* [Flawed enforcement of business rules](business-logic-vulnerabilities/flawed-enforcement-of-business-rules.md)

## Authentication vulnerabilities

* [Username enumeration via different responses](authentication/username-enumeration-via-different-responses.md)
* [2FA simple bypass](authentication/2fa-simple-bypass.md)
* [Password reset broken logic](authentication/password-reset-broken-logic.md)
* [Username enumeration via subtly different responses](authentication/username-enumeration-via-different-responses.md)

## Command Injection

* [OS command injection, simple case](command-injection/os-command-injection-simple-case.md)
* [Blind OS command injection with time delays](command-injection/blind-os-command-injection-with-time-delays.md)
* [Blind OS command injection with output redirection](command-injection/blind-os-command-injection-with-output-redirection.md)

## Path Traversal

* [File path traversal, simple case](path-traversal/file-path-traversal-simple-case.md)
* [File path traversal, traversal sequences blocked with absolute path bypass](path-traversal/file-path-traversal-traversal-sequences-blocked-with-absolute-path-bypass.md)
* [File path traversal, traversal sequences stripped non-recursively](path-traversal/file-path-traversal-traversal-sequences-stripped-non-recursively.md)
* [File path traversal, traversal sequences stripped with superfluous URL-decode](path-traversal/file-path-traversal-traversal-sequences-stripped-with-superfluous-url-decode.md)
* [File path traversal, validation of start of path](path-traversal/file-path-traversal-validation-of-start-of-path.md)
* [File path traversal, validation of file extension with null byte bypass](path-traversal/file-path-traversal-validation-of-file-extension-with-null-byte-bypass.md)

## Server-side request forgery

* [Basic SSRF against the local server](server-side-request-forgery-ssrf/basic-ssrf-against-the-local-server.md)
* [Basic SSRF against another back-end system](server-side-request-forgery-ssrf/basic-ssrf-against-another-back-end-system.md)
* [SSRF with blacklist-based input filter](server-side-request-forgery-ssrf/ssrf-with-blacklist-based-input-filter.md)

## Information disclosure

* [Information disclosure in error messages](information-disclosure/information-disclosure-in-error-messages.md)
* [Information disclosure on debug page](information-disclosure/information-disclosure-on-debug-page.md)
* [Source code disclosure via backup files](https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files)
* [Authentication bypass via information disclosure](information-disclosure/authentication-bypass-via-information-disclosure.md)

## Access control

* [Unprotected admin functionality](access-control/unprotected-admin-functionality.md)
* [Unprotected admin functionality with unpredictable URL](access-control/unprotected-admin-functionality-with-unpredictable-url.md)
* [User role controlled by request parameter](access-control/user-role-controlled-by-request-parameter.md)
* [User role can be modified in user profile](access-control/user-role-can-be-modified-in-user-profile.md)
* [User ID controlled by request parameter](access-control/user-id-controlled-by-request-parameter.md)
* [User ID controlled by request parameter, with unpredictable user IDs](access-control/user-id-controlled-by-request-parameter-with-unpredictable-user-ids.md)
* [User ID controlled by request parameter with data leakage in redirect](access-control/user-id-controlled-by-request-parameter-with-data-leakage-in-redirect.md)
* [User ID controlled by request parameter with password disclosure](access-control/user-id-controlled-by-request-parameter-with-password-disclosure.md)
* [Insecure direct object references](access-control/insecure-direct-object-references.md)
* [URL-based access control can be circumvented](access-control/url-based-access-control-can-be-circumvented.md)
* [Method-based access control can be circumvented](access-control/method-based-access-control-can-be-circumvented.md)
* [Multi-step process with no access control on one step](access-control/multi-step-process-with-no-access-control-on-one-step.md)
* [Referer-based access control](access-control/referer-based-access-control.md)

## XXE injection

* [Exploiting XXE using external entities to retrieve files](xxe-injection/exploiting-xxe-using-external-entities-to-retrieve-files.md)
* [Exploiting XXE to perform SSRF attacks](xxe-injection/exploiting-xxe-to-perform-ssrf-attacks.md)
