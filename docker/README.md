# overtls
```bash
docker run --restart always -p 80:80 -p 443:443/tcp -p 443:443/udp --name overtls -e TUNNEL_PATH=/secret-tunnel-path/ -v /cert:/cert -v /web:/web -itd chengxudong2020/overtls
```

# 参数说明
- `-p` supports HTTP3 when ports are mapped to host machine's 443 TCP and UDP ports.
- `-v certificate directory` must be mapped to the `/cert` container directory. The certificate directory must contain the private key `privkey.pem` and public key `fullchain.pem`. If the names don't match, please rename them.
- `-v web static files directory` Must contain any one of `index.php`, `index.html`, `index.htm`, `index.nginx-debian.html` as the default homepage. Please download from the internet and place in the directory, then restart the container, or prepare a new container in advance. The mapped directory in the container must be `/web`.
- `-e TUNNEL_PATH` Default format is `/secret-tunnel-path/` or `/secret-tunnel-path/,/secret-tunnel-path2/,/secret-tunnel-path2/`. Please make sure to modify it to complex characters.
- `-v Wireguard config directory` may be mapped to the `/etc/wireguard` container directory. The certificate directory must contain the default config `default.conf` to start Wireguard vpn at boot time.
