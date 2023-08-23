openssl req -new -newkey rsa:2048 -days 365 -extensions v3_ca -subj "/CN=localhost" -nodes -x509 -sha256 -set_serial 0 -keyout newcert.key -out newcert.cer


openssl req -newkey rsa:2048 -subj "/CN=localhost" -nodes -sha256 -keyout newcert.key -out newcert.csr -config .\openssl.cnf

openssl req -in newcert.csr -out newcert.pem

openssl x509 -req -in newcert.pem -signkey newcert.key -out newcert.crt




```
[ req ]
default_bits           = 2048
distinguished_name     = req_distinguished_name
req_extensions         = req_ext


[ req_distinguished_name ]
countryName            = IR
stateOrProvinceName    = IR
localityName           = IR
organizationName       = IR
commonName             = localhost

[ req_ext ]
subjectAltName = @alt_names

[alt_names]
DNS.1   = localhost
DNS.2   = localhost:3004
```
