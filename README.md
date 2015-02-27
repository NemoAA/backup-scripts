hppt
====

High Performance PostgreSQL Tools

Production quality programs for monitoring and tuning a busy PostgreSQL installation.
Tools are broken into rep (replication) and perf (performance) directories.

Configuration
=============

The database used for all the perf scripts can be set two ways with environment
variables::

    export HPPTDATABASE="db01"
    export HPPTOPTS="-d db01"

Using HPPTDATABASE is simpler, working like the built-in PGDATABASE environment
variable.  Using HPPTOPTS instead directly adds entries to the psql command line,
allowing you to add any additional information needed for these scripts to run
in your environment.

TODO
====

* There are some hard-coded things in these programs that should be
  more flexible input parameters.  The model for how everything should
  look eventually is the fully command line parameterized
  rep/archive_wal program.  Ideally needing to use environment variables
  for the database to connect to shouldn't even be necessary, if instead
  you'd prefer to pass options to every script you call.

* Right now the worst script needing cleanup is rep/restore-archive-file since
  it has a hard-coded archive directory name with no way to set that.
  rep/restore-archive-file has a similar issue.

* Several of the connection monitoring scripts in perf use pg_stat_activity, and
  they will not work against PostgreSQL 9.2 or later versions due to a change in
  that version.

License
=======

Copyright 2013-2015 Gregory Smith gsmith@westnet.com
2-Clause BSD Licensed; see LICENSE for details.
