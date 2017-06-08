# stats.jrw.fi

## Setup

Remember to create users & DB's:

    curl -X POST https://stats-db.jrw.fi/query --data-urlencode "q=CREATE USER agent WITH PASSWORD 'SECRET' WITH ALL PRIVILEGES"
    curl -X POST --user agent:SECRET https://stats-db.jrw.fi/query --data-urlencode "q=CREATE DATABASE home_jrw_fi"

Finally, log into Grafana, and add a new data source of type `influxdb` and host `http://influxdb:8086`.

## Notes

Useful links:

* https://blog.laputa.io/try-influxdb-and-grafana-by-docker-6b4d50c6a446
* http://docs.grafana.org/installation/configuration/#using-environment-variables

Add `influxdb` env var:

    - INFLUXDB_HTTP_WRITE_TRACING=true

to see what clients are writing to the DB.

To allow anonymous viewers, add `grafana` env vars:

    - GF_AUTH_ANONYMOUS_ENABLED=true
    - GF_AUTH_ORG_ROLE=Viewer

