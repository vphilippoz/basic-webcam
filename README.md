# Basic Webcam
## Goal
This tutorial shows how to setup a Raspberry Pi from scratch to turn it into a live webcam acessible from anywhere. It is not the most optimized or reliable setup, but it is simple and works.

## Material
- Raspberry Pi 3B+ or better
- USB camera (webcam or other). Pi camera is not supported.
- SD card

## Tutorial
### Outline 

1. Install latest Raspberry Pi OS and update
2. Install and configure video stream using `motion`
3. Configure firewall using `ufw`
4. Setup VPN access using `tailscale`
5. Reboot and test

### 1. Install Raspberry Pi OS
Do it using Raspberry Pi Imager. Select the correct board and most recent OS. Configure Wifi and SSH now, while it is easily done.

After booting the Rapsberry Pi, input the following commands in a terminal:
1. `sudo apt update`
2. `sudo apt upgrade`

### 2. Video stream

1. Install motion: `sudo apt-get install motion`
2. Save a backup of the original configuration: `sudo cp /etc/motion/motion.conf /etc/motion/motion.conf.bckp`
3. Configure motion: `sudo nano /etc/motion/motion.conf`

   3.1. `text_left RD Webcam 1`

   3.2. `movie_output off`

   3.3. `stream_localhost off`

### 3. Firewall
Requests from client devices must be let through the firewall. The port of the video stream must be opened. To do that, Uncomplicated Firewall (`ufw`) is the best tool.

1. Install ufw: `sudo apt-get install ufw`
2. Activate it: `sudo ufw enable`
3. Open port 8081: `sudo ufw allow 8081`
4. Check that it worked: `sudo ufw status`

### 4. Remote access

1. Install `tailscale`: Follow the instructions on [Tailscale website](https://tailscale.com/download/linux/)
2. Register the device on your tailscale net: `sudo tailscale up`
3. Copy the link provided on a web browser (phone, computer, ...) and authenticate the device.
4. From the same web page, disable the key expiry

### 5. Reboot and test

1. Reboot the Raspberry Pi: `sudo reboot`
2. When it is up again, connect a device on the same Tailscale network (for example, a smartphone) and open `http://<Raspberry Pi IPv4 address>:8081`
3. You should see the live video feed of the USB camera.

## Debugging

If connection is refused, check the firewall configuration. Live stream should work locally on `http://127.0.0.1:8081` on the Raspberry Pi. If it's not the case, check the configuration of motion or the USB camera. **Pi Camera do not work with motion !**
