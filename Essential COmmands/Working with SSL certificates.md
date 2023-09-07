- Certificates authenticate and encrypt the connections 
```zsh 
#create tls and ssh certs
# on linuz we use oopen ssl --> creation of x.509 certificates

```

## Certificate Signing Requests CSRs
- generate a CSR
- send the CSR to a CA 
- then other site check with CA to ensure cert validity

## creating SSL certs 
```zsh
# create priate key and generate a cert request
openssl req -newkey rsa:2048 -keyout key.pem -out req.pem

# generate self signed root certificate
openssl req -x509 -noenc -newkey rsa:4096 -days 365-keyout key.pem -out req.pem


```
