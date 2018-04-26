# PostgreSQL bash backup script.

Local or remote PostgreSQL backup script written in bash.

This script is a wrapper arround pg_dump and pg_dumpall

## Requirements

Those package MUST be installed on your system:

* bash ( >= 4 )
* postgresql-client ( >= 8.4 )

Version not in that range MAY work but are not tested.

My home made logger: f_notify

## Release note

Semantic versioning is used to define version (https://semver.org/)

https://github.com/JGroselle/pgbackup/blob/master/RELEASE_NOTE.md

## Getting started

Checkout this repository or copy pgbackup in an appropiate folder.

Ex. /usr/local/bin

It is RECOMMENDED to deploy it where your DBA can execute it.

Check PATH environment variable of postgres user.

## Usage

User SHOULD execute `pgbackup -h` to see all the available options.

Regarding remote backup, user SHOULD create a dedicated PostgreSQL backup role.

Here is mine, superuser with read-only trasaction:

    $ createuser -P -e -E -s $role_name
    ALTER USER $role_name set default_transaction_read_only = on;

## Configuration file

The configuration file MUST be in a `key=value` format (bash readable)

An example is available in this repository, in conf.d/pgbackup.conf.sample.

Feel free to use it. `cp conf.d/pgbackup.conf.sample /etc/pgbackup.conf`

User SHOULD take a look at this file to make the PosgreSQL backup suit his needs.

## Examples

Backup all local databases:

`pgbackup -a`

Backup a local database named testdb:

`pgbackup -b testdb`

Backup all remote databases:

`pgbackup -a -r postgresql.example.net`

Backup a remote database named testdb:

`pgbackup -b testdb -r postgresql.example.net`

__NOTE:__ remote backup MUST need a pgpass file.

Please refer to the offial documentation:

https://www.postgresql.org/docs/current/static/libpq-pgpass.html

## Contribute

If you find a bug, please report it here: https://github.com/JGroselle/pgbackup/issues

If you want add some feature, feel free to make a PR. ;)

## Note

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL

NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and

"OPTIONAL" in this document are to be interpreted as described in

RFC 2119.
