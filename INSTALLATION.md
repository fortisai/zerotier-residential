# ZeroTier and Squid Proxy Setup Guide for Raspberry Pi/Server

This guide will walk you through setting up a ZeroTier network and configuring a Squid proxy server on a Raspberry Pi or similar device in your local network.

## 1. Create a ZeroTier Network

1. Go to [my.zerotier.com](https://my.zerotier.com/) and sign in or create an account.
2. Click "Create A Network".
3. Note down the Network ID.
4. Under "IPv4 Auto-Assign", set a range (e.g., 172.27.0.0/16).
5. Set Access Control to "Private".

## 2. Install and Configure ZeroTier on Raspberry Pi

```bash
curl -s https://install.zerotier.com | sudo bash
sudo zerotier-cli join YOUR_NETWORK_ID
```

Replace YOUR_NETWORK_ID with the ID noted earlier.

## 3. Authorize the Raspberry Pi

1. Go back to my.zerotier.com and select your network.
2. Find your Raspberry Pi in the "Members" list.
3. Check the "Auth" checkbox to authorize it.

## 4. Install and Configure Squid

```bash
sudo apt update
sudo apt install squid -y

# Backup original config
sudo cp /etc/squid/squid.conf /etc/squid/squid.conf.bak

# Edit Squid config
sudo nano /etc/squid/squid.conf
```

Add or modify these lines in the config:

```
http_port 3128
acl localnet src 172.27.0.0/16  # Your ZeroTier network range
http_access allow localnet
http_access deny all
```

Save and exit.

## 5. Start and Enable Squid

```bash
sudo systemctl restart squid
sudo systemctl enable squid
```

## 6. Configure Firewall (if applicable)

If you're using UFW:

```bash
sudo ufw allow from 172.27.0.0/16 to any port 3128
```

Your Raspberry Pi is now set up with ZeroTier and Squid. The proxy will be accessible to any device on your ZeroTier network.