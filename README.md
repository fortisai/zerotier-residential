# ZeroTier Residential Proxy

## Overview

This project sets up a residential proxy using a Raspberry Pi (or similar device) on your home network, accessible from anywhere via ZeroTier. It allows you to route your internet traffic through your home network, effectively using your home IP address while browsing from any location.

## Features

- **Remote Access**: Access your home network securely from anywhere.
- **IP Masking**: Browse the internet using your home IP address, regardless of your physical location.
- **No Port Forwarding**: Works without configuring port forwarding on your home router.
- **Cross-Platform**: Compatible with various operating systems (instructions provided for macOS).

## Components

1. **ZeroTier**: A software-defined networking tool that creates a secure, global virtual network of devices.
2. **Squid**: A caching and forwarding HTTP web proxy, used to route traffic on the Raspberry Pi.
3. **Raspberry Pi**: Acts as the proxy server within your home network (can be substituted with other always-on devices).

## How It Works

1. ZeroTier creates a virtual network connecting your devices.
2. Squid runs on the Raspberry Pi, acting as a proxy server.
3. Your remote device connects to the ZeroTier network and uses the Raspberry Pi as a proxy.
4. All internet traffic from your remote device is routed through your home network.

## Setup

The setup process is divided into two main parts:

1. **Server Setup** (INSTALLATION.md): 
   - Creating a ZeroTier network
   - Configuring ZeroTier and Squid on a Raspberry Pi

2. **Client Setup** (SETUP.md):
   - Installing and configuring ZeroTier on a macOS client
   - Setting up proxy settings to use the Raspberry Pi

Detailed instructions for each part can be found in the respective markdown files.
