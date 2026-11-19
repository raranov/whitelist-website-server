# whitelist-website

A login-gated CONNECT proxy for the timed tablets. Recorded 18 Nov 2026 from the Cursor plan `tablet_tunnel_proxy`. Nothing is built yet.

The proxy runs on the album Pi (`10.100.102.55`). The Pi Zero (`10.100.102.19`) stays DNS and Caddy. It does not carry the page traffic.

- Portal on port 8790, reached as `browse.home` through Caddy on the Zero.
- CONNECT proxy on port 3128. It does not decrypt TLS. Only port 443 is forwarded. LAN targets are refused.
- Accounts, host rules, a daily window, and daily minutes live in this app's own SQLite file, timezone `Asia/Jerusalem`. A login grants the tablet's source IP. When the window ends or the minutes run out, that IP is revoked and its open tunnels are closed.
- Layout on the Pi: `/opt/whitelist-website`, `/var/lib/whitelist-website/app.sqlite`, `/etc/whitelist-website/app.env`.

The app and its tests land in this repo before anything is installed on the Pi.
