# docker-metasploit

[Metasploit](http://metasploit.com) is a penetration testing and vulnerability mitigation tool. This is a Docker configuration for getting metasploit running without having to install it locally. It does not include a database, you'll have to provide that on your own.

## What's in it

- Metasploit dpkg build (dev-4.13.3-2016112910301)
- nmap (for `db_nmap` in msfconsole)

## How to use it

```bash
$ docker run -d --name msf-postgres -e POSTGRES_USER=msf -t postgres:latest
$ docker run -i --link msf-postgres:postgres -p 8080:8080 -t mdouglas/metasploit
```

In this example, port 8080 is mapped so that you can set `RPORT` to that number, and `RHOST` is the IP of your machine.

Then, inside of msfconsole:
```
> db_connect msf@postgres/msf
```

## Extras

If you want to save your msf settings elsewhere, mount a volume to `/root/.msf4`.
