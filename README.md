# Setup-and-Use-a-Firewall-on-Windows-Linux
Configure and test firewall rules on Windows Defender Firewall and Kali Linux (UFW). Includes commands, screenshots, and a detailed report demonstrating how to block/allow ports, test connections, and understand network traffic filtering.
1. Tools

Windows Defender Firewall with Advanced Security (Windows 10/11)

UFW on Kali Linux

Telnet / Netcat for testing

2. Environment

Windows Host: Windows 10/11

Linux Host: Kali Linux Rolling

Local network setup for testing blocked/allowed connections.

3. Procedure
Windows

Opened Windows Defender Firewall with Advanced Security.

Viewed inbound rules.

Created a rule to block TCP port 23 (Telnet).

Tested connection with telnet <windows_IP> 23 — connection failed as expected.

Removed the rule to restore default configuration.

Kali Linux

Enabled UFW and checked current status with sudo ufw status verbose.

Added a deny rule for port 23: sudo ufw deny 23/tcp.

Ensured SSH (port 22) remained open with sudo ufw allow 22/tcp.

Tested the rule using nc -vz <kali_IP> 23 — connection failed as expected.

Removed the test rule using sudo ufw delete deny 23/tcp.

4. Commands Used
    Get-NetFirewallRule | Where-Object { $_.Direction -eq 'Inbound' } | Format-Table -AutoSize
New-NetFirewallRule -DisplayName "Block Telnet" -Direction Inbound -LocalPort 23 -Protocol TCP -Action Block
Remove-NetFirewallRule -DisplayName "Block Telnet"

Kali Linux Terminal
sudo ufw enable
sudo ufw status verbose
sudo ufw deny 23/tcp
sudo ufw allow 22/tcp
nc -vz <kali_IP> 23 # test connection
sudo ufw delete deny 23/tcp

5. Observations

Blocking port 23 successfully prevented Telnet connections.

Allowing SSH maintained remote access to Kali.

Both Windows and Linux firewalls effectively filtered traffic based on port and protocol.

6. Outcome

Successfully configured and tested firewall rules on Windows and Kali Linux. Gained practical knowledge of firewall management and network traffic filtering.

7. Evidence

See screenshots and configuration outputs:
![Windows-Defender](https://github.com/user-attachments/assets/8ef84af0-f9b2-4250-a333-c22c3b1f08ac)
![Kalilinux-Firewall](https://github.com/user-attachments/assets/687da8f7-cb3f-4f98-b679-6f90dd61d105)

