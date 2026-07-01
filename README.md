# 🚀 XUI.ONE 1.5.13 Ubuntu 22.04 Installer

Ready-to-use **XUI.ONE 1.5.13 installer package for Ubuntu 22.04 LTS / Jammy**.

This package is prepared for users who want to install **XUI.ONE 1.5.13 on Ubuntu 22.04** quickly and easily.

Run the commands, enter your activation code, and let the installer prepare everything for you.

> ⚠️ Use this installer only with XUI.ONE files and activation codes you are authorized to use.
> Do not share your activation code, MySQL credentials, or private server details publicly.

---

## ✅ Supported System

| Software | Version           |
| -------- | ----------------- |
| XUI.ONE  | 1.5.13             |
| Ubuntu   | 22.04 LTS / Jammy |

---

## 📦 Download

Installer ZIP:

```text
https://github.com/RootWebCore/xui-one-1513-ubuntu22-installer/releases/download/v1.5.13/xui-one-1513-ubuntu22-installer.zip
```

Package contents:

```text
database.sql
install
xui.tar.gz
```

---

## 🔑 Activation Code

During installation, the installer will ask for your activation code:

```text
Enter license key:
```

You can get your activation code from:

```text
https://rootwebcore.byethost33.com
```

When the installer asks for the license key, enter the activation code you received from this page.

---

## ⚡ Quick Installation

Run the following commands on a clean Ubuntu 22.04 server:

```bash
sudo apt update
sudo apt install zip unzip wget -y

cd /tmp
wget https://github.com/rootwcore/xui-one-1513-ubuntu22-installer/releases/download/v1.5.13/xui-one-1513-ubuntu22-installer.zip

unzip xui-one-153-ubuntu22-installer.zip
cd /tmp/xui

sed -i 's/\r$//' install
chmod +x install
sudo ./install
```

During installation, you may see:

```text
Overwrite sysctl configuration? Recommended! (Y / N):
```

Recommended answer:

```text
Y
```

Then enter your activation code:

```text
Enter license key: YOUR_ACTIVATION_CODE
```

That is all. Sit back and let the installer prepare the system for you.

---

## 🌐 Panel Access

At the end of installation, the installer will show your panel setup URL:

```text
Continue Setup: http://YOUR_SERVER_IP/ACCESS_CODE/
```

Open this URL in your browser and continue the setup.

Use the URL exactly as printed by the installer.

---

## 🔍 Check Status

After installation, you can check XUI.ONE status with:

```bash
/home/xui/status
```

Expected result:

```text
Status
------------------------------
XUI is running.

Database
------------------------------
Connected successfully.

License
------------------------------
License expires: ...
```

---

## 🔄 Restart XUI.ONE

To restart XUI.ONE manually:

```bash
sudo systemctl restart xuione
```

Or:

```bash
sudo /home/xui/service restart
```

Then check status again:

```bash
/home/xui/status
```

---

## 🔥 Firewall Notes

HTTP access must be allowed.

If UFW is enabled:

```bash
sudo ufw allow 80/tcp
sudo ufw reload
```

If your hosting provider has a cloud firewall, allow inbound TCP port:

```text
80
```

For streaming usage, also allow the ports required by your own XUI.ONE configuration.

---

## 🧾 MySQL Credentials

The installer will generate MySQL credentials automatically.

At the end of installation, it will print:

```text
MySQL Username: GENERATED_USERNAME
MySQL Password: GENERATED_PASSWORD
```

It will also save them here:

```text
/tmp/xui/credentials.txt
```

Move this file somewhere safe:

```bash
mv /tmp/xui/credentials.txt /root/xui-credentials.txt
chmod 600 /root/xui-credentials.txt
```

---

## 🧯 Troubleshooting

### Panel does not open

Check status:

```bash
/home/xui/status
```

Check port 80:

```bash
ss -tulpn | grep ':80'
```

Restart XUI.ONE:

```bash
sudo systemctl restart xuione
sleep 5
/home/xui/status
```

---

### Activation code is not detected

Check config:

```bash
grep -n '^license' /home/xui/config/config.ini
```

Restart service:

```bash
sudo systemctl restart xuione
/home/xui/status
```

---

### Port 80 is not accessible

Allow HTTP traffic:

```bash
sudo ufw allow 80/tcp
sudo ufw reload
```

Also check your hosting provider firewall and allow inbound TCP port `80`.

---

## 🛡️ Security Notes

* Do not publish your activation code.
* Do not publish MySQL credentials.
* Move `credentials.txt` to a safe location after installation.
* Do not expose MariaDB or Redis publicly.
* Keep your firewall properly configured.
* Use this installer only with XUI.ONE files and activation codes you are authorized to use.

---

## ⚖️ License Notice

This repository does not grant any rights to redistribute proprietary XUI.ONE files.

Use only with XUI.ONE files and activation codes you are authorized to use.
