# Vector & Influx as a SIEM

Trying vector.dev and InfluxDB to test an SIEM as an alternative to usual ELK stacks.

## Why ?

I discovered vector.dev. Also the ELK stack is cool but I tend to prefer InfluxDB since
it's Go over Java, that's not enough of an argument but hey, let's have fun!

## Quickstart

- Create `influx.env` and `aggregator.env` files:

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

_aggregator.env_
```sh
INFLUXDB_ORG=vector-org
INFLUXDB_BUCKET=vector-bucket
INFLUXDB_TOKEN=<token from influxdb>
```

- `$ chmod +x start`
- `$ ./start`, you should be good to go and Influx should be available on `localhost:8086`.