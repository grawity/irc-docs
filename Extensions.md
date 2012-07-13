## ISUPPORT (current; all ircds)

Only advertises extensions; they are assumed to be always enabled, unless declared otherwise. (For example, `UHNAMES` has to enabled by client.) [Draft specification](http://www.irc.org/tech_docs/draft-brocklesby-irc-isupport-03.txt) exists.

Known extensions:

 * [`WHOX`](http://hg.quakenet.org/snircd/file/37c9c7460603/doc/readme.who)
 * [List of other extensions](http://www.irc.org/tech_docs/005.html)

## CAP (current; many ircds)

Part of [IRCv3](http://ircv3.atheme.org/). Implemented by most major ircds according to [draft specification](http://ircv3.atheme.org/specification/capability-negotiation-3.1).

Known extensions:

 * [`account-notify`](http://ircv3.atheme.org/extensions/account-notify-3.1)
 * [`away-notify`](http://ircv3.atheme.org/extensions/away-notify-3.1)
 * [`extended-join`](http://ircv3.atheme.org/extensions/extended-join-3.1)
 * `identify-msg`
 * [`multi-prefix`](http://ircv3.atheme.org/extensions/multi-prefix-3.1)
 * [`sasl`](http://ircv3.atheme.org/extensions/sasl-3.1)
 * [`tls`](http://ircv3.atheme.org/extensions/tls-3.1)
 * `userhost-in-names`

Features:

 * Server acknowledges successful and failed requests.
 * Can disable extensions (using `CAP REQ -foo`).
 * Can list extensions during registration (using `CAP LS`).

## CAPAB (obsolete; Hyperion)

Known extensions:

 * `IDENTIFY-MSG` – identical to CAP `identify-msg`

Features:

 * Server acknowledges successful requests.

Downsides:

 * Server does not acknowledge failed requests.
 * Cannot disable extensions once enabled.
 * Extensions are only advertised after registration (in ISUPPORT).

## PROTOCTL (deprecated; UnrealIRCd, several others)

Known extensions:

 * `UHNAMES` – identical to CAP `userhost-in-names`
 * `NAMESX` – identical to CAP `multi-prefix`

Downsides:

 * Server does not acknowledge requests.
 * Cannot disable extensions once enabled.
 * Extensions are only advertised after registration (in ISUPPORT).