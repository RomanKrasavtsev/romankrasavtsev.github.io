# Telegraf + InfluxDB + Chronograf + Kapacitor

## InfluxDB
 - install

## Telegraf
 - install
 - edit config
 - restart service [sudo service telegraf restart]
### Config
```
  sudo vim /etc/telegraf/telegraf.conf
```
 
#### Telegraf
```
 28 interval = "1m"
 73 hostname = ""
```

#### InfluxDB
```
 88   urls = ["http://localhost:8086"]
 90   database = "telegraf"
```

#### Disk
```
 496 [[inputs.disk]]
 499   mount_points = ["/"]
```

#### MySQL
```
 1191 [[inputs.mysql]]
 1200   servers = ["tcp(127.0.0.1:3306)/"]
 1213   gather_process_list                       = true
 1219   gather_slave_status                       = true
 # 1225   gather_table_io_waits                     = false
```

#### NGNIX
```
1284 [[inputs.nginx]]
1286   urls = ["http://localhost/status"]
```

#### Unicorn
```
1462   pid_file = "/var/run/unicorn.pid"
```

#### Redis
```
1542 [[inputs.redis]]
1552   servers = ["tcp://localhost:6379"]
```

## Chronograf
```
  docker run -d -p 10000:10000 chronograf
```
