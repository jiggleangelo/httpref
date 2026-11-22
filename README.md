# httpref

Original MIT original offline browser tool. Open index.html directly. Analyze a status code and response header lines, or expand Generate headers from fields and create a draft. Generator replaces header input, adds Vary: Origin for a non-wildcard origin, and uses the same analyzer. Reports and draft are separately copyable; clipboard denial selects text manually. All edits invalidate results. No requests, storage, server, dependencies or external assets. Use fictional header values; exported reports contain the supplied headers.

## Scope

Bundled status reference covers common named 1xx–5xx codes, including WebDAV. Every three-digit 100–599 code is accepted; unlisted codes warn. This is a constant reference, not a complete/current registry. 305 is deprecated, 306/418 unused; 510 is historical. Category and bodyAllowed are descriptive: 1xx/204/304 forbid response bodies; HEAD and 205 require additional handling. Generated HTTP/1.1 text is a review draft, not a complete wire response (no body/framing/CRLF terminator is generated).

Header syntax requires printable ASCII, horizontal tabs in values, LF/CRLF, and token names directly followed by a colon. Empty lines are ignored; continuation/folded lines, bare CR, controls and non-ASCII fail. Unknown headers are preserved with lowercase names and trimmed values; their semantics are not validated. Cache-Control instances combine; duplicate CORS singleton/list fields error. Other header duplication is not validated.

Cache-Control: quote-aware comma parsing, escapes in quoted values, duplicate names, integer seconds (including quoted seconds), valueless flags, optional max-stale seconds, quoted field-name lists for private/no-cache, public/private conflicts, no-store reuse warnings, private/s-maxage warnings, no-cache revalidation explanation. Unknown extension semantics are not inferred. No request/response context, Age/Date/Expires, validators, shared/private cache behavior, request directive validity, heuristic freshness or actual cache execution is modeled.

CORS: Allow-Origin accepts *, null, or one canonical serialized web origin with no path, default port spelling, userinfo, list or trailing slash. URL parsing is local, never a request. Credentials must be exactly true if present. Wildcard origin with credentials errors. null warns. Request-varying origins should use Vary: Origin; unconditional constant origins can trigger a conservative warning. Token lists, method casing, wildcard/credential semantics, explicit Authorization requirement and bounded nonnegative Max-Age are checked. Browser caps are not predicted. Missing Allow-Origin with other CORS fields warns. This response-only tool has no request origin/mode, preflight transaction or credential context; actual browser access is not determined. Request headers, private-network extensions, CORP, COEP and CSP policy are outside scope. CORS is not authentication.

Limits: 65536 UTF-16 input units, 500 lines, bounded integer seconds. Malformed header structure, unterminated cache quote and limits throw with no output; semantic findings return valid=false on errors while retaining a visibly advisory draft. Generator rejects newline/control injection and analyzes all generated fields. No automatic corrections or live policy deployment.

MIT LICENSE included. All test data are fictional.


## Run, test and fork

Open `index.html` beside the supplied JavaScript and CSS files, or use any static server. Run the tests with `node --test` in this folder (Node 22 or later); they need no network. Fork the MIT source and retain its license.

[Tool page](https://manykiln.com/tools/httpref/) · [Source code](https://github.com/jiggleangelo/httpref) · [Join the list](https://join.manykiln.com/?from=httpref) · [Privacy](https://manykiln.com/privacy)
