```bash
client

dev tun
proto tcp
remote 34.118.85.76 1194

persist-key
persist-tun

;user nobody
;group nobody

nobind
resolv-retry infinite

# Certificates
# ca as <ca></ca>
# cert <cert></cert>
# key <key></key>

# Auth / Encryption
auth SHA512
cipher AES-256-CBC

remote-cert-tls server
verify-x509-name server_rj5GdAW6ZWXw7Bqj name

# TLS
tls-client
tls-version-min 1.2
tls-cipher TLS-ECDHE-ECDSA-WITH-AES-128-GCM-SHA256
# tls-crypt as <tls-crypt></tls-crypt>

#setenv opt block-outside-dns   # DNS Leaks windows
#dhcp-option DOMAIN-ROUTE .     # Linux
#dhcp-option DNS 8.8.8.8
#dhcp-option DNS 8.8.4.4
#route 3.232.242.170 255.255.255.255
#route 52.20.78.240 255.255.255.255
#route 3.220.57.224 255.255.255.255
#route 54.91.59.199 255.255.255.255
#route 10.100.10.0 255.255.255.0
#route 10.100.20.0 255.255.255.0

verb 3

<ca>
</ca>
<cert>
</cert>
<key>
</key>
<tls-crypt>
</tls-crypt>
```

## Linux raw connection workaround

`required`
```bash
apt-get install -y openvpn-systemd-resolved
```

```bash
script-security 2
up /etc/openvpn/update-systemd-resolved
down /etc/openvpn/update-systemd-resolved
down-pre
```
