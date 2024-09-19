# macOS ZeroTier and Proxy Configuration Guide

This guide will walk you through setting up ZeroTier on a macOS machine and configuring it to use a Squid proxy server.

## 1. Install ZeroTier on macOS

1. Go to [zerotier.com/download](https://www.zerotier.com/download/)
2. Download and install the macOS client.

## 2. Join ZeroTier Network

1. Open ZeroTier on your macOS device.
2. Click "Join Network".
3. Enter your ZeroTier Network ID.
4. Click "Join".

## 3. Authorize the macOS Device

1. Go to [my.zerotier.com](https://my.zerotier.com/) and sign in.
2. Select your network.
3. Find your macOS device in the "Members" list.
4. Check the "Auth" checkbox to authorize it.

## 4. Configure Proxy Settings

1. Click the Apple menu and select "System Preferences".
2. Click on "Network".
3. Select your active network connection (e.g., Wi-Fi or Ethernet).
4. Click "Advanced".
5. Go to the "Proxies" tab.
6. Check the boxes for "Web Proxy (HTTP)" and "Secure Web Proxy (HTTPS)".
7. For both, enter:
   - Server: [Your Raspberry Pi's ZeroTier IP]
   - Port: 3128
8. Click "OK", then "Apply".

To find your Raspberry Pi's ZeroTier IP, you can run this command on the Raspberry Pi:
```
sudo zerotier-cli listnetworks
```

## 5. Verify the Connection

1. Open a web browser.
2. Look up "my ip" or a similar query to check your IP address.
3. It should show your home network's IP address, indicating that you're using the proxy.

## 6. Disabling the Proxy

To disable the proxy and return to your normal internet connection, follow these steps:

1. Disable the proxy settings:
   - Open "System Preferences" > "Network"
   - Select your active network connection (e.g., Wi-Fi or Ethernet)
   - Click "Advanced"
   - Go to the "Proxies" tab
   - Uncheck the boxes for "Web Proxy (HTTP)" and "Secure Web Proxy (HTTPS)"
   - Click "OK", then "Apply"

2. Disconnect from ZeroTier:
   - Open ZeroTier on your macOS device
   - Click "Leave Network"

Remember to re-enable both of these settings when you want to use the residential proxy again.


## 6. (Optional) Use Terminal with Proxy

To use the proxy in Terminal sessions, you can set environment variables:

```bash
export http_proxy=http://[RaspberryPi_ZeroTier_IP]:3128
export https_proxy=http://[RaspberryPi_ZeroTier_IP]:3128
```

Replace [RaspberryPi_ZeroTier_IP] with your Raspberry Pi's actual ZeroTier IP address.

You're now connected to your ZeroTier network and using your Raspberry Pi as a proxy server. All your internet traffic will appear to come from your home network's IP address.