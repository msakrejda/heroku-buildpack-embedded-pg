# Heroku Embedded Postgres Buildpack

This buildpack will configure a Postgres server to start on dyno boot
inside the dyno. It runs on the default Postgres port 5432 on
localhost.

Note that for UNIX socket connections, the `psql` binary in dynos
expects a unix socket file at `/run/postgresql`, and the Postgres from
this buildpack uses `/tmp`. Only the `postgres` database is created by
default.

To connect, run

```
psql --host /tmp postgres
```

N.B.: the data written to this Postgres instance only exists within
the ephemeral dyno filesystem, and thus will be lost when the dyno
cycles. This buildpack is only useful for a continuous integration
setup, experiments, or other transient usage; it cannot function as a
data store.
