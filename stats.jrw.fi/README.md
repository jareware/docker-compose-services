# stats.jrw.fi

## Setup

Add HTTP authentication for the host by adding:

    ../nginx-proxy/htpasswd/stats-db.jrw.fi

Remember to create a new DB with:

    curl -i -XPOST --user agent:SECRET https://stats-db.jrw.fi/query --data-urlencode "q=CREATE DATABASE home_jrw_fi"

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

