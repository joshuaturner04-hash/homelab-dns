\# Homelab DNS (dnsmasq)



A `dnsmasq` config providing wildcard local DNS resolution for `\*.home` hostnames across the homelab LAN, paired with \[Nginx Proxy Manager](https://nginxproxymanager.com/) reverse-proxy hosts.



\## What it does



\- Forwards all normal DNS queries upstream to the router

\- Resolves any `\*.home` hostname directly to the Nginx Proxy Manager box, which then routes to the correct internal service based on hostname



\## Setup



Copy `dnsmasq.conf` to `/etc/dnsmasq.conf` on a dedicated lightweight LXC, then:



```bash

systemctl restart dnsmasq

systemctl enable dnsmasq

```



Point client devices' DNS at this box's IP (either network-wide via your router, or per-device).



