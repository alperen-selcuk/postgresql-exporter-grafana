# postgresql-exporter-grafana

first you need to install postgresql exporter binary

https://github.com/prometheus-community/postgres_exporter

than copy the your local binary directory.

```
sudo cp postgres_exporter /usr/local/bin
```

after that create a directory and put a env file.

```
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
