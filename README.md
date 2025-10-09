# Basic Webcam
## Goal
This tutorial shows how to setup a Raspberry Pi from scratch to turn it into a live webcam acessible from anywhere. It is not the most optimized or reliable setup, but it is simple and works.

## Outline
1. Install latest Raspberry Pi OS and update
2. Install and configure video stream using `motion`
3. Configure firewall using `ufw`
4. Setup VPN access using `tailscale`

## 1. Install Raspberry Pi OS
Do it using Raspberry Pi Imager. Select the correct board and most recent OS. Configure Wifi and SSH now, while it is easily done.

## 2. Video stream

## 3. Firewall
Requests from client devices must be let through the firewall. The port of the video stream must be opened. To do that, Uncomplicated Firewall (`ufw`) is the best tool.

1. Install `ufw`:
2. Activate it:
3. Open port 8081:

## 4. Remote access

1. Install `tailscale`:
2. Register the device on your tailscale net:
