# Heroku Embedded Postgres Buildpack

This buildpack will configure a Postgres server to start on dyno boot
inside the dyno. It injects a `DATABASE_URL` environment variable into
your app that behaves like a config var.
To connect, run

```
psql $DATABASE_URL
```

N.B.: the data written to this Postgres instance only exists within
the ephemeral dyno filesystem, and thus will be lost when the dyno
cycles. This buildpack is only useful for a continuous integration
setup, experiments, or other transient usage; it cannot function as a
data store.
