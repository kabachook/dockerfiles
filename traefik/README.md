# Traefik basic conf

* `docker create network web`
* Tweak everything in `traefik.toml`
* Add your services to `docker-compose.yml` or set `--network web` and traefik labels to your containers
* `chmod 600 acme.json` or traefik won't get access to it

> Dashboard in on `monitor.yourdomain.com`
>
> Automatically gets SSL certificates from Let's encrypt on all of your subdomains used
