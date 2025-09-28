# cy-task4
# Firewall Configuration: Block Telnet and Allow SSH

## Objective

This guide explains how to configure the Windows Firewall to **block Telnet (port 23)** and **allow SSH (port 22)** on a Windows 10 machine.

---

## 1. Open Windows Firewall with Advanced Security

1. Press `Windows + S` and search for **Windows Defender Firewall**.
2. Select **Windows Defender Firewall** from the results.
3. Click **Advanced settings** in the left pane to open **Windows Firewall with Advanced Security**.

---

## 2. Block Telnet (Port 23)

Telnet is an insecure protocol. Blocking port 23 helps prevent unauthorized remote access.

### GUI Method

1. In **Windows Firewall with Advanced Security**, go to **Inbound Rules**.
2. Click **New Rule**.
3. Choose **Port**, then click **Next**.
4. Select **TCP** and enter **23** as the port.
5. Choose **Block the connection** and click **Next**.
6. Apply to **Domain**, **Private**, and **Public** profiles.
7. Name the rule (e.g., "Block Telnet") and click **Finish**.

---

## 3. Allow SSH (Port 22)

SSH (Secure Shell) is used for secure remote access.

### GUI Method

1. In **Windows Firewall with Advanced Security**, go to **Inbound Rules**.
2. Click **New Rule**.
3. Choose **Port**, then click **Next**.
4. Select **TCP** and enter **22** as the port.
5. Choose **Allow the connection** and click **Next**.
6. Apply to **Domain**, **Private**, and **Public** profiles.
7. Name the rule (e.g., "Allow SSH") and click **Finish**.

---

## 4. Verify the Configuration

### Check Telnet Block

```cmd
telnet <IP_Address> 23
```

You should see a connection error indicating Telnet is blocked.

### Check SSH Access

```cmd
ssh <username>@<IP_Address>
```

## 5. Remove the Rules (Optional)

To remove these firewall rules:

```cmd
netsh advfirewall firewall delete rule name="Block Telnet"
netsh advfirewall firewall delete rule name="Allow SSH"
```

---
## 6. Remove the Test Block Rule

Go back to the Inbound Rules section in Windows Firewall with Advanced Security.

Find the rule you created (e.g., "Block Telnet" and "allow SSH").
