# expiration date

## ftp
```
openssl s_client -connect $DOMAIN:21 -starttls ftp <<< "" 2>/dev/null | openssl x509 -noout -enddate | cut -d = -f 2
```
