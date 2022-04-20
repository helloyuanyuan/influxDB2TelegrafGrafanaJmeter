# InfluxDB2 + Telegraf + Grafana + Jmeter Demo

## Steps

### 1. run InfluxDB2, Telegraf and Grafana with docker compose

   docker-compose -f docker-compose.yml up -d

### 2. config InfluxDB2 + Telegraf

- InfluxDB2: <http://localhost:8086/signin> admin / admin123
- InfluxDB2: Data > Token (tab) > Generate R/W API token (button) > select R/W bucket to save
- projectDir: Copy the generated token > write it to ./telegraf/telegraf.com > token = "$INFLUX_TOKEN"
- Docker: restart telegraf
- InfluxDB2: check Telegraf data be generated in bucket > DemoBucket (cpu, disk, mem, etc...)
- InfluxDB2: create dashboard and alert

### 3. config Grafana + InfluxDB2

- Grafana: <http://localhost:3000> admin / admin -> skip change password
- config -> data source -> add data source
- select InfluxDB as template
- select Flux as language
- close basic auth
- Add URL: <http://influxdb2:8086> -> save & test
- create new dashboard and select InfluxDB data source

### 4. config Jmeter + InfluxDB2

- InfluxDB2: create new bucket > jmeter
- Jmeter: add backend listener > <http://localhost:8086/api/v2/write?org=DemoOrg&bucket=jmeter>
