# Restoring Network Connection After Deleting Network Manager

## Introduction
If you have accidentally deleted Network Manager on a Linux system, you may lose network connectivity. This guide documents the process of manually reconnecting to Wi-Fi and reinstalling Network Manager.

---

## Steps to Restore Connectivity

### 1. Obtain a Dynamic IP Address
Since Network Manager is missing, you need to manually request an IP address for your wireless interface (`wlan0`). Run the following command:
```bash
sudo dhclient wlan0
```
This will attempt to obtain an IP address from the DHCP server.

### 2. Identify Available Wireless Networks
To check if your wireless interface can detect available networks, use:
```bash
sudo iwlist wlan0
```
or
```bash
sudo iwlist wlan0 scanning
```
This will display a list of available Wi-Fi networks.

### 3. Connect to a Wireless Network
To manually associate with a Wi-Fi network, use:
```bash
sudo iwconfig wlan0 ssid "oranjo"
```
Replace `oranjo` with the SSID of your preferred network.

To verify the connection, run:
```bash
iwconfig
```
This command shows the current wireless connection status.

---

## Updating System Packages
Before reinstalling Network Manager, update your package list to ensure you get the latest versions:
```bash
sudo apt update && sudo apt upgrade -y
```

## Reinstalling Network Manager
Once connected, you can restore Network Manager by reinstalling the necessary packages:
```bash
sudo apt install -y network-manager network-manager-gnome wpasupplicant wireless-tools ifupdown
```
This command reinstalls:
- `network-manager`: Manages network connections.
- `network-manager-gnome`: GUI for managing network connections.
- `wpasupplicant`: Handles WPA/WPA2 authentication.
- `wireless-tools`: Provides tools for wireless network management.
- `ifupdown`: Helps bring interfaces up and down.

### 4. Reboot the System
To apply the changes, restart your machine:
```bash
sudo reboot
```
After rebooting, Network Manager should be fully functional again, allowing you to manage network connections normally.

---

## Conclusion
By following these steps, you can regain network connectivity and reinstall Network Manager on your Linux system after accidental deletion. These commands help manually configure Wi-Fi and restore automated network management.

