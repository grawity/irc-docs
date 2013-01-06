# IRC protocol extensions

## Original IRC protocol

 * [grawity's collected docs](https://github.com/grawity/irc-docs)

Original protocol (IRCv2): [RFC 1459][rfc1459]

Later updated by [RFC 2810][rfc2810], [RFC 2811][rfc2811], [RFC 2812][rfc2812], [RFC 2813][rfc2813], but few servers follow these completely. IRCnet is probably the most complete implementation.

Client-server protocol:

 * [Jilles' IRC protocol documentation](http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/)
 * [IRC v3 Working Group][ircv3]

Server-server protocol:

 * TS (Hybrid → Charybdis)
     * Versions: [TS3][ts3], [TS5][ts5], [TS6][ts6], [TS6 v7][ts6v7], [TS6 v8][ts6v8]
     * Extensions: [ENCAP][ts-encap], various [CAPAB][ts-capab]'s
     * TS6-specific: [EUID][ts6-euid], [SAVE][ts6-save]
 * [P10][p10] (ircu)

  [rfc1459]: http://tools.ietf.org/html/rfc1459
  [rfc2810]: http://tools.ietf.org/html/rfc2810
  [rfc2811]: http://tools.ietf.org/html/rfc2811
  [rfc2812]: http://tools.ietf.org/html/rfc2812
  [rfc2813]: http://tools.ietf.org/html/rfc2813
  [ts3]: https://github.com/grawity/irc-docs/blob/master/server/ts3.txt
  [ts5]: https://github.com/grawity/irc-docs/blob/master/server/ts5.txt
  [ts6]: https://github.com/grawity/irc-docs/blob/master/server/ts6.txt
  [ts6v7]: https://github.com/grawity/irc-docs/blob/master/server/ts6v7.txt
  [ts6v8]: https://github.com/grawity/irc-docs/blob/master/server/ts6v8.txt
  [ts-encap]: http://www.leeh.co.uk/ircd/encap.txt
  [ts-capab]: https://github.com/grawity/irc-docs/blob/master/server/ts-capab.txt
  [ts6-save]: https://github.com/grawity/irc-docs/blob/master/server/ts6-save-collision-fnc.txt
  [ts6-euid]: https://github.com/grawity/irc-docs/blob/master/server/ts6-euid.txt
  [p10]: http://web.mit.edu/klmitch/Sipb/devel/src/ircu2.10.11/doc/p10.html
  [ircv3]: http://ircv3.atheme.org/

## CTCP and DCC

**Client-To-Client Protocol** (CTCP) messages are carried over standard PRIVMSGs and NOTICEs. The [original specification][ctcp] allows for quoting special characters, sending "extended data" and commands.

However, most clients do not implement the quoting, and only recognize messages consisting entirely of a single "extended data" command.

 * [Later CTCP draft][ctcp-1997] (no known implementations)
 * [Later CTCP/2 draft][ctcp2] (no known implementations)

IRCII introduced the **Direct Client Connection** (DCC) subprotocol. Often, "DCC" refers specifically to the file transfer part.

 * [DCC protocol][dcc-ircii] as implemented by IRCII
 * [Turbo DCC][dcc-turbo] (entire file as bytestream)
 * [Reverse DCC][dcc-reverse] (receiver listens for connection)
 * FSERV (opens a chat session with FTP-like commands)
 * [XDCC][dcc-xdcc] 

 [ctcp]: http://www.irchelp.org/irchelp/rfc/ctcpspec.html
 [ctcp-1997]: http://web.archive.org/web/20100209042300/http://www.invlogic.com/irc/ctcp.html
 [ctcp2]: http://web.archive.org/web/20080723170128/http://www.invlogic.com/irc/ctcp2_intro.html
 [dcc-ircii]: http://www.irchelp.org/irchelp/rfc/dccspec.html
 [dcc-turbo]: http://www.visualirc.net/tech-tdcc.php
 [dcc-reverse]: http://cvs.epicsol.org/cgi/viewcvs.cgi/epic5/doc/DCC_REVERSE?rev=1.4
 [dcc-xdcc]: http://xa.bi/files/irc/xdcc.3.3.0b.irc

## User identification

 * SASL (IRCv3 style)
 * SASL (IRCX style)
 * privileged bots – NickServ, Q
 * RFC 1459 server password (`PASS` command)
 * [Ident][rfc1413] (OS-level authentication)

 [rfc1413]: http://tools.ietf.org/html/rfc1413

## Capability negotiation

 * The 005 numeric, aka `RPL_ISUPPORT`
 * IRCv3 `CAP`
 * Dancer/Hyperion `CAPAB`
 * `PROTOCTL`
 * Microsoft IRCX

## ISUPPORT

Implemented by almost all servers. Only advertises extensions; they are assumed to be always enabled, unless declared otherwise. (For example, `UHNAMES` has to enabled by client.) Many extensions in ISUPPORT deal with core IRC features; for example, supported channel types (e.g. `CHANTYPES=#&`) or the longest permitted nickname (`NICKLEN`).

Draft specifications:

 * [E. Brocklesby, 2004][isupport-eb-2004]
 * [Lee Hardy, 2005][isupport-leeh-2005]

Known extensions:

 * [List of common extensions][isupport-list]
 * [`CALLERID`][callerid]
 * [`MONITOR`][monitor] and [`WATCH`][watch]
 * [`WHOX`][whox]

  [isupport-eb-2004]: http://tools.ietf.org/html/draft-brocklesby-irc-isupport-03
  [isupport-leeh-2005]: http://tools.ietf.org/html/draft-hardy-irc-isupport-00
  [isupport-list]: http://www.irc.org/tech_docs/005.html
  [callerid]: http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/54870aec98e4/reference/modeg.txt
  [monitor]: http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/54870aec98e4/reference/monitor.txt
  [watch]: http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/54870aec98e4/reference/draft-meglio-irc-watch-00.txt
  [whox]: http://hg.quakenet.org/snircd/file/37c9c7460603/doc/readme.who

## CAP and IRCv3

The **IRCv3 Working Group** defines a standard set of extensions to IRCv2. The central part of IRCv3 is [capability negotiation][v3-cap] using `CAP`, which is implemented by all current servers.

Known extensions:

 * [account notification][v3-account-notify] (Charybdis, Unreal)
 * [away notification][v3-away-notify] (Charybdis, Unreal)
 * [extended JOIN][v3-extended-join] (Charybdis, Unreal)
 * `identify-msg` (Charybdis)
 * [multi-prefix NAMES][v3-multi-prefix]
 * [message tags][v3-message-tags] (ZNC)
 * [metadata][v3-metadata]
 * [server time][v3-server-time] (ZNC)
 * [SASL authentication][v3-sasl] (Atheme, Anope)
 * [STARTTLS][v3-tls] (InspIRCd, Unreal)
 * `userhost-in-names` – equivalent to NAMESX (Unreal)

Features:

 * Server acknowledges successful and failed requests.
 * Can disable extensions (using `CAP REQ -foo`).
 * Can list extensions during registration (using `CAP LS`).

Downsides:

 * For `sasl`, supported SASL mechanisms are not advertised. (This may be fixed soon.)

  [v3-cap]: http://ircv3.atheme.org/specification/capability-negotiation-3.1
  [v3-account-notify]: http://ircv3.atheme.org/extensions/account-notify-3.1
  [v3-away-notify]: http://ircv3.atheme.org/extensions/away-notify-3.1
  [v3-extended-join]: http://ircv3.atheme.org/extensions/extended-join-3.1
  [v3-multi-prefix]: http://ircv3.atheme.org/extensions/multi-prefix-3.1
  [v3-sasl]: http://ircv3.atheme.org/extensions/sasl-3.1
  [v3-server-time]: http://ircv3.atheme.org/extensions/server-time-3.2
  [v3-tls]: http://ircv3.atheme.org/extensions/tls-3.1
  [v3-message-tags]: http://ircv3.atheme.org/specification/message-tags-3.2
  [v3-metadata]: http://ircv3.atheme.org/specification/metadata-3.2

## CAPAB (obsolete; Hybrid, Dancer, Hyperion)

Known extensions:

 * `IDENTIFY-MSG` – identical to CAP `identify-msg`
 * `IDENTIFY-CTCP` (Dancer) – merged into `IDENTIFY-MSG` by Hyperion

Features:

 * Server acknowledges successful requests.

Downsides:

 * Server does not acknowledge failed requests.
 * Cannot disable extensions once enabled.
 * Extensions are only advertised after registration (in ISUPPORT).

## PROTOCTL (deprecated; Dreamforge, UnrealIRCd)

Known extensions:

 * `UHNAMES` – identical to CAP `userhost-in-names`
 * `NAMESX` – identical to CAP `multi-prefix`

Downsides:

 * Server does not acknowledge requests.
 * Cannot disable extensions once enabled.
 * Extensions are only advertised after registration (in ISUPPORT).

## HANDSHAKE (obsolete; never used)

[Draft specification][handshake-draft].

Known extensions (listed in draft):

 * [`CHARSET`][handshake-charset]
 * [`LANGUAGE`][handshake-language]
 * `NAMESX` – identical to CAP `multi-prefix`

Features:

 * Extensions can be enabled during registration.
 * Server acknowledges successful requests.

Downsides:

 * Cannot request extensions after registration.
 * Cannot disable extensions once enabled.
 * Supported extensions are not advertised by the server (the client must request all extensions it wants).

 [handshake-draft]: http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/tip/reference/draft-meglio-irc-handshake-00.txt
 [handshake-charset]: http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/tip/reference/draft-meglio-irc-handshake-00.txt#l287
 [handshake-language]: http://www.stack.nl/~jilles/cgi-bin/hgwebdir.cgi/irc-documentation-jilles/file/tip/reference/draft-meglio-irc-handshake-00.txt#l312

## IRCX (obsolete; Microsoft)

An extension of the IRC protocol as a whole, used by Microsoft Chat client as well as Microsoft Exchange Chat server.

Edited [draft specification][ircx-draft] exists; it describes several new commands implemented by IRCX-compatible servers, as well as modes and privilege levels. Adds SASL support using `AUTH`, predating CAP.

There are plans to add several IRCX features to IRCv3.

Features:

 * Extension must be enabled during registration (using `IRCX`).
 * All supported extensions are part of the specification.
 * Supported SASL mechanisms are advertised by server during registration.

 [ircx-draft]: http://static.ignition-project.com/ircxdraft/
