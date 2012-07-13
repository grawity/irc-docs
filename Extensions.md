## `CAP`

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

## `CAPAB` (Hyperion)

Known extensions:

 * `IDENTIFY-MSG` – identical to CAP `identify-msg`

Features:

 * Server acknowledges successful requests.

Downsides:

 * Server does not acknowledge failed requests.
 * Cannot disable extensions once enabled.
 * Extensions are only advertised after registration (in ISUPPORT).

## `PROTOCTL` (UnrealIRCd, several others)

Known extensions:

 * `UHNAMES` – identical to CAP `userhost-in-names`
 * `NAMESX` – identical to CAP `multi-prefix`

Downsides:

 * Server does not acknowledge requests.
 * Cannot disable extensions once enabled.
 * Extensions are only advertised after registration (in ISUPPORT).

## Miscellaneous