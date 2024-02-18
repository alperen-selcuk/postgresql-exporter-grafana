# postgresql-exporter-grafana

for this repo you can get all postgresql metrics to grafana

## postgresql exporter

first you need to install postgresql exporter binary

https://github.com/prometheus-community/postgres_exporter

than copy the your local binary directory.

```
sudo cp postgres_exporter /usr/local/bin
```

after that create a directory and put a env file.

```
mkdir -p /opt/postgres_exporter
cd /opt/postgres_exporter
touch postgres_exporter.env
```

type your posgres connection string

```
echo DATA_SOURCE_NAME="postgresql://postgres:$DB_USER@#DB_IP:5432/?sslmode=disable" >> postgres_exporter.env
```

create postgres user and add system file for postgres service. file already i creates on repository.

```
sudo useradd -rs /bin/false postgres
vi /etc/systemd/system/postgres_exporter.service
```

sudo systemctl daemon-reload
sudo systemctl start postgres_exporter
sudo systemctl enable postgres_exporter
sudo systemctl status postgres_exporter

## prometheus

after collect metrics with postgresql exporter you need to send this metrics through prometheus. and put local bin directory.

https://github.com/prometheus/prometheus

```
sudo cp prometheus /usr/local/bin
```

create prometheus directory for prometheus config yaml. configuration has already in repo.

```
mkdir -p /opt/prometheus
cd /opt/prometheus
touch prometheus.yml
```

after created yml file you can run prometheys as a service like postgresql_exporter.

```
sudo useradd -rs /bin/false prometheus
vi /etc/systemd/system/prometheus.service
```
