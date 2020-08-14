# Docker: Multiple Domain Support
## Features
- PHP (7.4.x & FPM)
- MySQL (8.x)
- SSL (certbot)

## Default URL
- web.local
- admin.local
- dbadmin.local

## Open SSL command
```sh
# web.local
openssl req -x509 -out web.local.crt -keyout web.local.key \
-newkey rsa:2048 -nodes -sha256 \
-subj '/CN=web.local' -extensions EXT -config <( \
printf "[dn]\nCN=web.local\n[req]\ndistinguished_name = dn\n[EXT]\nsubjectAltName=DNS:web.local\nkeyUsage=digitalSignature\nextendedKeyUsage=serverAuth")

# admin.local
openssl req -x509 -out admin.local.crt -keyout admin.local.key \
-newkey rsa:2048 -nodes -sha256 \
-subj '/CN=admin.local' -extensions EXT -config <( \
printf "[dn]\nCN=admin.local\n[req]\ndistinguished_name = dn\n[EXT]\nsubjectAltName=DNS:admin.local\nkeyUsage=digitalSignature\nextendedKeyUsage=serverAuth")
```

## HINTs
**Windows** 

Update server name in "hosts" file at "C:\Windows\System32\drivers\etc"
```sh
127.0.0.1 web.local admin.local
```
Refresh DNS with this command
```sh
ipconfig /flushdns
```