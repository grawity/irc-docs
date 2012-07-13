See also:

 * [Jilles' IRC protocol documentation](http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/)
 * [IRC v3 Working Group](http://ircv3.atheme.org/)

## ISUPPORT (current; all ircds)

Only advertises extensions; they are assumed to be always enabled, unless declared otherwise. (For example, `UHNAMES` has to enabled by client.) Many extensions in ISUPPORT deal with core IRC features; for example, supported channel types (e.g. `CHANTYPES=#&`) or the longest permitted nickname (`NICKLEN`).

Implemented by almost all ircds. [Draft specification](http://www.irc.org/tech_docs/draft-brocklesby-irc-isupport-03.txt) exists.

Known extensions:

 * [`CALLERID`](http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/54870aec98e4/reference/modeg.txt)
 * [`MONITOR`](http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/54870aec98e4/reference/monitor.txt) and [`WATCH`](http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/54870aec98e4/reference/draft-meglio-irc-watch-00.txt)
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

Downsides:

 * For `sasl`, supported SASL mechanisms are not advertised. (This may be fixed soon.)

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

## HANDSHAKE (never used)

[Draft specification](http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/tip/reference/draft-meglio-irc-handshake-00.txt).

Known extensions (listed in draft):

 * [`CHARSET`](http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/tip/reference/draft-meglio-irc-handshake-00.txt#l287)
 * [`LANGUAGE`](http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/tip/reference/draft-meglio-irc-handshake-00.txt#l312)
 * `NAMESX` – identical to CAP `multi-prefix`

Features:

 * Extensions can be enabled during registration.
 * Server acknowledges successful requests.

Downsides:

 * Cannot request extensions after registration.
 * Cannot disable extensions once enabled.
 * Supported extensions are not advertised by the server (the client must request all extensions it wants).

## IRCX (obsolete; Microsoft)

An extension of the IRC protocol as a whole, used by Microsoft Chat client as well as Microsoft Exchange Chat server.

Edited [draft specification](http://static.ignition-project.com/ircxdraft/) exists; it describes several new commands implemented by IRCX-compatible servers, as well as modes and privilege levels. Adds SASL support using `AUTH`, predating CAP.

Features:

 * Extension must be enabled during registration (using `IRCX`).
 * All supported extensions are part of the specification.
 * Supported SASL mechanisms are advertised by server during registration.