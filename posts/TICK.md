# Telegraf + InfluxDB + Chronograf + Kapacitor

## InfluxDB
 - install

## Telegraf
 - install
 - edit config
```
  sudo vim /etc/telegraf/telegraf.conf
```
 - restart service 
```
  sudo service telegraf restart
```
 - check
```
  telegraf -config /etc/telegraf/telegraf.conf -test
```
### Config
 
#### Telegraf
```
 28 interval = "10m"
 70   logfile = "/var/log/telegraf/plugins.txt"
 73   hostname = ""
```

#### InfluxDB
```
 88   urls = ["http://localhost:8086"]
 90   database = "telegraf"
```

#### CPU
```
488   percpu = false
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
 1210   gather_table_schema                       = true
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
1459 [[inputs.procstat]]
1462   pid_file = "/var/www/shared/pids/unicorn.pid"
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
