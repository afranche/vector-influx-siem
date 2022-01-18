# Vector & Influx as a SIEM

Trying vector.dev and InfluxDB to test both as alternative to usual ELK stacks for SIEM usage.

Nothing too fancy, it barely works. I discovered [vector.dev](https://vector.dev) a few weeks
ago but I didn't get more information until now I found the time for it. I like Datadog so I
figured out this tool would be cool. I'm using a centralized aggregator with an agent that
sends random logs to it, supposedly it is more cost-effective than having a stream-based approach
but you could miss out on some logs out here (adding Apache Kafka and testing it out is a TODO).

InfluxDB is purely a naive choice out here, I already tested out ELK and it's cool, but if I
have the occasion to pick Go over Java I'm doing it. Also, this project is not focused towards
having the fastest stack, I'm mainly discovering new ways of doing things without taking
benchmarks into account for now.

## Quickstart

- Create `influx.env`, `grafana.env` and `aggregator.env` files:

_influx.env_
```sh
INFLUXDB_HTTP_BIND_ADDRESS=":8086"
DOCKER_INFLUXDB_INIT_MODE=setup
DOCKER_INFLUXDB_INIT_USERNAME=<username of your choice>
DOCKER_INFLUXDB_INIT_PASSWORD=<password of your choice>
DOCKER_INFLUXDB_INIT_ORG=vector-org
DOCKER_INFLUXDB_INIT_BUCKET=vector-bucket
DOCKER_INFLUXDB_INIT_ADMIN_TOKEN=<token of your choice>
```

_grafana.env_
```sh
GF_SECURITY_ADMIN_USER=<username of your choice>
GF_SECURITY_ADMIN_PASSWORD=<password of your choice>
GF_PATHS_PROVISIONING=/opt/provisioning
INFLUXDB_URL=http://influxdb:8086
INFLUXDB_TOKEN=<token from influxdb>
```

_aggregator.env_
```sh
INFLUXDB_ORG=vector-org
INFLUXDB_BUCKET=vector-bucket
INFLUXDB_TOKEN=<token from influxdb>
```

- `$ chmod +x start`
- `$ ./start`, you should be good to go and Influx should be available on `localhost:8086`.