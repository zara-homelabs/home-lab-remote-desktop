# home-lab-remote-desktop
Virtual lab project configuring Remote Desktop between Windows 11 and Ubuntu 22.04 using VMware.

🖥 Virtual Lab – Remote Desktop Configuration
📌 Project Overview

Built a virtual lab using VMware Workstation to configure remote desktop access between Windows 11 and Ubuntu 22.04.

This project demonstrates hands-on experience with:

Virtualisation

Host-only networking

IP configuration

Linux service management

Remote Desktop Protocol (RDP)

Troubleshooting display/session conflicts

🧱 Environment

Host OS: Windows 11
VM1: Ubuntu 22.04 LTS
VM2: Windows 11 Pro
Network Mode: Host-Only

🌐 Network Configuration

Configured both virtual machines on Host-Only networking.

Ubuntu IP: 192.168.126.128
Windows IP: 192.168.126.129

Connectivity validated using:

ping <IP address>
🛠 Remote Desktop Setup (Ubuntu)

Installed xrdp:

sudo apt update
sudo apt install xrdp -y
sudo systemctl enable xrdp
sudo systemctl start xrdp
🐛 Issue Encountered – Wayland Conflict
Problem

RDP session disconnected immediately after connecting.

Error observed:

ibus notification should be called from the desktop session in wayland
Root Cause

Ubuntu 22.04 uses Wayland by default, which is not fully compatible with xrdp.

Resolution

Installed XFCE desktop environment and configured session manually:

sudo apt install xfce4 xfce4-goodies -y
echo xfce4-session > ~/.xsession
sudo systemctl restart xrdp

After configuration, RDP connection succeeded.

📚 Key Learning Outcomes

Understanding of NAT vs Host-only networking

Remote desktop configuration in Linux

Service management using systemctl

Diagnosing display/session conflicts

Practical troubleshooting workflow
