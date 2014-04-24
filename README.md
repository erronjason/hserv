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
		if ($host = 'myv') {
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
127.0.0.1 intranet myv store www
```

####Append to .bashrc:

```
export PATH=$PATH:$HOME/bin/
```

###Usage:
(console | shutdown | start | stop)

Use "hserv start" to start the vagrant VM and all projects, then "hserv console" to attach to the associated screen session. Using "ctrl+a" then "n" will allow you to cycle though the windows, and "ctrl+a" then "d" will detach you from the session. "hserv stop" closes the screen session and all python servers, but not the vagrant vm. To shut down the vagrant vm, use "hserv shutdown".
