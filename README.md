# Docker: Multiple Domain Support
---
## Features
- PHP (7.4.x & FPM)
- MySQL (8.x)
- SSL (certbot)

## Default URL
- web.local
- admin.local

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