# generate github CR PAT
# generate Cloudflare PAT

# opening ports
sudo apt-get install firewalld
sudo systemctl enable firewalld
sudo systemctl start firewalld
sudo firewall-cmd --zone=public --add-port=80/tcp --permanent # or --add-service=http
sudo firewall-cmd --zone=public --add-port=443/tcp --permanent # or --add-service=http
sudo firewall-cmd --reload

sudo iptables -P FORWARD ACCEPT

# DO NOT USE SNAP DOCKER
# CHECK CLOUDFLARE DNS SETTINGS SSL FULL STRICT
# PUT THE STUPID CLOUDFLARE API TOKEN FORM .ENV IN ./data/certbot/cloudflare.ini

export CR_PAT=
echo $CR_PAT | sudo docker login ghcr.io -u lmihaig --password-stdin
this generates in -> /root/.docker/config.json.

<!-- # file for caddy with cloudflare addon, not used rn -->
<!-- FROM caddy:builder AS builder
RUN caddy-builder \
    github.com/caddy-dns/cloudflare
FROM caddy:latest
COPY --from=builder /usr/bin/caddy /usr/bin/caddy -->
