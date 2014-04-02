hserv
=====

Automate starting Hivelocity internal projects as a singular entity

## Setup

Place contents in $HOME/bin/<br>
chmod +x hserv

####Add to nginx /etc/nginx/sites-available/default:

```
server {
	location / {
		if ($host = 'www') {
			proxy_pass http://127.0.0.1:5040;
		}
		if ($host = 'my') {
			proxy_pass http://127.0.0.1:5045;
		}
		if ($host = 'intranet') {
			proxy_pass http://127.0.0.1:5050;
		}
		if ($host = 'store') {
			proxy_pass http://127.0.0.1:5055;
		}
	}
}
```

####Append to localhost line in /etc/hosts:

```
127.0.0.1 intranet my store www
```

####Append to .bashrc:

```
export PATH=$PATH:$HOME/bin/
```

###Usage:
hserv (start | stop)
