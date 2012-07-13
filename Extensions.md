## CAP

Known extensions:

 * [`account-notify`](http://ircv3.atheme.org/extensions/account-notify-3.1)
 * `away-notify`
 * `extended-join`
 * `identify-msg`
 * `multi-prefix`
 * `sasl`
 * `tls`
 * `userhost-in-names`

Features:

 * Server acknowledges successful and failed requests.
 * Can disable extensions (using `CAP REQ -foo`).
 * Can list extensions during registration (using `CAP LS`).

## CAPAB (Hyperion)

Known extensions:

 * `IDENTIFY-MSG` – identical to CAP `identify-msg`

Features:

 * Server acknowledges successful requests.

Downsides:

 * Server does not acknowledge failed requests.
 * Cannot disable extensions once enabled.
 * Extensions are only advertised after registration (in ISUPPORT).

## PROTOCTL (UnrealIRCd, several others)

Known extensions:

 * `UHNAMES` – identical to CAP `userhost-in-names`
 * `NAMESX` – identical to CAP `multi-prefix`

Downsides:

 * Server does not acknowledge requests.
 * Cannot disable extensions once enabled.
 * Extensions are only advertised after registration (in ISUPPORT).

## ISUPPORT (all ircds)

Only advertises extensions; they are assumed to be always enabled, unless declared otherwise. (For example, `UHNAMES` has to enabled by client.)

 * [`WHOX`](http://hg.quakenet.org/snircd/file/37c9c7460603/doc/readme.who)
 * [several other extensions](http://www.irc.org/tech_docs/005.html)