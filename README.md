# 🌐 Network-Troubleshooting.md

# 🛠️ Network Troubleshooting & Connectivity Guide

This guide covers common network issues encountered by users and the step-by-step process to resolve them in a corporate or home environment.

---

## 💻 Essential Command Prompt (CMD) Tools
Use these commands to diagnose connection issues quickly.


| Command | Purpose |
| :--- | :--- |
| `ipconfig /all` | 📋 Displays all current TCP/IP network configuration values. |
| `ping [IP/Domain]` | 📡 Tests connectivity to a specific server (e.g., `ping google.com`). |
| `tracert [Domain]` | 📍 Shows the path a packet takes to reach a destination. |
| `nslookup [Domain]` | 🔍 Checks if DNS is correctly resolving the domain name. |
| `netsh winsock reset` | 🔄 Resets the network adapter to default settings. |

---

## 🛠️ Common Scenarios & Fixes

### 🚫 "No Internet Access" or "Limited Connectivity"
**Issue:** The user is connected to Wi-Fi/Ethernet but cannot browse the web.
1. 🖥️ Open CMD as Administrator.
2. ⌨️ Run the following commands in order:
   - `ipconfig /release` (Drops current IP) 💧
   - `ipconfig /renew` (Requests a new IP from DHCP) ✨
   - `ipconfig /flushdns` (Clears corrupted DNS cache) 🧹
3. 🌐 Restart the browser and check.

### 🌐 DNS Server Not Responding
**Issue:** User can use apps like WhatsApp/Teams but cannot open websites in a browser.
1. ⚙️ Go to **Control Panel > Network and Sharing Center**.
2. 🖱️ Click **Change adapter settings**.
3. 📑 Right-click your connection > **Properties > IPv4**.
4. 🛠️ Change DNS to Google DNS:
   - Preferred: `8.8.8.8`
   - Alternate: `8.8.4.4`
5. ✅ Click OK and restart the connection.

### 📶 Wi-Fi Not Showing Available Networks
**Issue:** The Wi-Fi list is empty or the Wi-Fi icon is missing.
1. ⌨️ Press `Win + X` and open **Device Manager**.
2. 📂 Expand **Network Adapters**.
3. 🗑️ Right-click your Wi-Fi driver (e.g., Intel/Realtek) and select **Uninstall device** (Do NOT delete driver software).
4. 🔍 Click **Action** at the top > **Scan for hardware changes**.
5. 🚀 The driver will reinstall automatically. Check the Wi-Fi list again.

### 🆔 Duplicate IP Address Conflict
**Issue:** Two devices on the network have the same IP, causing one to disconnect.
1. ⌨️ Run `ipconfig /release` and `ipconfig /renew` on the affected machine.
2. ✏️ If it's a static IP, manually change the last digit of the IP address in **IPv4 Settings**.

---

## 💡 Quick Tips for Help Desk
- **🔑 VPN Issues:** Always ask the user to disconnect and reconnect the VPN if they can't access internal folders.
- **🔌 Physical Check:** For desktops, ensure the LAN cable is firmly plugged in (Look for the green/orange light).


| Network Issue | Diagnostic Tool | Primary Fix |
| :--- | :--- | :--- |
| **📉 Intermittent Disconnects** | `ping -t 8.8.8.8` | Check for physical cable damage or Wi-Fi interference. |
| **❌ DNS Resolution Failure** | `nslookup` / `dig` | Switch to Google DNS (8.8.8.8) or Flush DNS Cache. |
| **🔄 IP Address Conflicts** | `ipconfig /renew` | Release and renew the DHCP lease. |
| **🐌 Slow Network Speeds** | `Task Manager` | Identify background apps consuming bandwidth. |
| **🔐 VPN Authentication Error** | VPN Client Logs | Verify system time/date and user credentials. |

### 📶 Wi-Fi Frequent Disconnects
**Issue:** Wi-Fi drops connection intermittently every few minutes.
- **✅ Fix:** Go to **Device Manager** > Network Adapters > Right-click Wi-Fi Driver > **Properties** > **Power Management**. Uncheck *"Allow the computer to turn off this device to save power."* 🔋

### 🔒 VPN Connected but Resources Unreachable
**Issue:** VPN is active, but internal shared drives or portals won't open.
- **✅ Fix:** Verify if the **DNS Suffix** for the company domain is added in Advanced TCP/IP settings. Use `tracert` to identify if traffic is routing through the VPN tunnel or local ISP. 🛤️

### 🧊 DHCP Address Pool Exhaustion
**Issue:** Devices stuck at "Obtaining IP Address" or receiving an APIPA address (169.254.x.x).
- **✅ Fix:** This indicates the DHCP server has run out of available IP addresses. Increase the **DHCP Scope** or reduce the **Lease Time** in the Router/Server settings. 📉

### 📂 Network Discovery & File Sharing Issues
**Issue:** Unable to see other PCs or Printers on the same local network.
- **✅ Fix:** 
  1. 🌐 Enable **Network Discovery** and **File/Printer Sharing** in Advanced Sharing Settings.
  2. ⚙️ Ensure the **"Function Discovery Resource Publication"** service is running in `services.msc`.

