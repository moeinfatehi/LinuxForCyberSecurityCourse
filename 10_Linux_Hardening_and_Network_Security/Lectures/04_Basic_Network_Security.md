# Basic Network Security

Network security is crucial in protecting your Linux system from external threats. This lecture will cover essential network security practices, including securing network services, configuring firewalls, using network monitoring tools, and setting up VPNs for secure remote access.

## 1. Securing Network Services

Network services are often the first point of attack for external threats. Properly securing these services is vital for maintaining a secure system.

### 1.1 Disabling Unused Network Services

Running unnecessary network services increases the attack surface of your system. It’s essential to disable or uninstall any services that are not needed.

#### Example: Disabling a Service

1. Identify running services:
   ```bash
   sudo netstat -tuln
   ```
2. Disable unnecessary services using `systemctl`:
   ```bash
   sudo systemctl stop service_name
   sudo systemctl disable service_name
   ```

### 1.2 Securing SSH Access

SSH is often targeted by attackers attempting to gain unauthorized access to your system. We've already covered how to secure SSH using key-based authentication, disabling root login, and implementing 2FA. Here, we'll reinforce the importance of limiting access to SSH.

#### Example: Restricting SSH Access by IP Address

1. Edit the SSH configuration file (`/etc/ssh/sshd_config`):
   ```bash
   AllowUsers user@192.168.1.100
   ```
   - This restricts SSH access to a specific user from a specific IP address.
2. Restart the SSH service:
   ```bash
   sudo systemctl restart sshd
   ```

### 1.3 Using TCP Wrappers to Restrict Access

TCP Wrappers can be used to restrict access to network services based on IP addresses. It provides an additional layer of access control on top of your firewall.

#### Example: Restricting Access to a Service

1. Edit the `/etc/hosts.allow` file to allow access:
   ```bash
   sshd: 192.168.1.100
   ```
2. Edit the `/etc/hosts.deny` file to deny access:
   ```bash
   ALL: ALL
   ```

## 2. Configuring Firewalls

Firewalls are essential for controlling incoming and outgoing traffic to your system. Configuring a firewall helps protect your system from unauthorized access.

### 2.1 Using `ufw` (Uncomplicated Firewall)

`ufw` is a simple and user-friendly tool for configuring firewalls on Debian-based systems.

#### Example: Basic Firewall Rules with `ufw`

1. Enable the firewall:
   ```bash
   sudo ufw enable
   ```
2. Allow specific services (e.g., SSH, HTTP, HTTPS):
   ```bash
   sudo ufw allow ssh
   sudo ufw allow http
   sudo ufw allow https
   ```
3. Deny all other incoming traffic by default:
   ```bash
   sudo ufw default deny incoming
   ```
4. Check the status of the firewall:
   ```bash
   sudo ufw status
   ```

### 2.2 Advanced Firewall Configuration with `iptables`

`iptables` provides more granular control over network traffic but requires more advanced configuration. It is available on most Linux distributions and offers powerful capabilities for creating custom firewall rules.

#### Example: Basic `iptables` Rules

1. Allow SSH traffic:
   ```bash
   sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
   ```
2. Allow HTTP traffic:
   ```bash
   sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
   ```
3. Drop all other incoming traffic:
   ```bash
   sudo iptables -P INPUT DROP
   ```

4. Save the firewall rules:
   - **Debian/Ubuntu**:
     ```bash
     sudo netfilter-persistent save
     ```
   - **CentOS/RHEL**:
     ```bash
     sudo service iptables save
     ```

### 2.3 Firewalld on CentOS/RHEL

For CentOS/RHEL systems, `firewalld` provides a dynamic firewall management tool with support for network zones.

#### Example: Basic `firewalld` Configuration

1. Enable and start `firewalld`:
   ```bash
   sudo systemctl enable firewalld
   sudo systemctl start firewalld
   ```
2. Allow services (e.g., SSH, HTTP, HTTPS):
   ```bash
   sudo firewall-cmd --permanent --add-service=ssh
   sudo firewall-cmd --permanent --add-service=http
   sudo firewall-cmd --permanent --add-service=https
   ```
3. Reload the firewall rules:
   ```bash
   sudo firewall-cmd --reload
   ```

## 3. Network Monitoring Tools

Monitoring your network is essential for detecting potential security breaches and diagnosing network issues. Several tools can help you monitor network traffic and activity.

### 3.1 Using `netstat` to Monitor Network Connections

`netstat` is a basic network tool that shows active network connections and listening ports.

#### Example: Displaying Active TCP Connections

```bash
netstat -tuln
```

- `-tuln`: Shows all listening TCP and UDP ports in numeric form.

### 3.2 Using `nmap` for Network Scanning

`nmap` is a powerful network scanning tool that can be used to discover open ports, running services, and potential vulnerabilities.

#### Example: Scanning for Open Ports on a Remote Host

```bash
nmap -sS 192.168.1.100
```

- `-sS`: Performs a TCP SYN scan, which is less likely to be detected by the target system.

### 3.3 Using `tcpdump` for Packet Analysis

`tcpdump` is a command-line packet analyzer that allows you to capture and analyze network traffic in real-time.

#### Example: Capturing Traffic on a Specific Interface

```bash
sudo tcpdump -i eth0
```

- This command captures all traffic on the `eth0` interface.

### 3.4 Using `iftop` for Real-Time Bandwidth Monitoring

`iftop` is a real-time network bandwidth monitoring tool that shows bandwidth usage per connection.

#### Example: Monitoring Bandwidth on an Interface

```bash
sudo iftop -i eth0
```

## 4. Introduction to VPNs for Secure Remote Access

Virtual Private Networks (VPNs) provide secure remote access to your network by encrypting all traffic between the client and the VPN server.

### 4.1 Setting Up OpenVPN

OpenVPN is a popular open-source VPN solution that can be used to create secure connections between remote users and your network.

#### Example: Basic OpenVPN Setup

1. Install OpenVPN:
   - **Debian/Ubuntu**:
     ```bash
     sudo apt-get install openvpn
     ```
   - **CentOS/RHEL**:
     ```bash
     sudo yum install openvpn
     ```

2. Configure the OpenVPN server using sample configuration files provided by the package.
3. Start the OpenVPN service:
   ```bash
   sudo systemctl start openvpn@server
   ```

### 4.2 Using WireGuard for VPN

WireGuard is a modern, lightweight VPN solution that offers high performance and simplicity compared to traditional VPNs like OpenVPN.

#### Example: Setting Up WireGuard

1. Install WireGuard:
   - **Debian/Ubuntu**:
     ```bash
     sudo apt-get install wireguard
     ```
   - **CentOS/RHEL**:
     ```bash
     sudo yum install wireguard-tools
     ```

2. Configure WireGuard using the provided sample configuration.
3. Start the WireGuard service:
   ```bash
   sudo wg-quick up wg0
   ```

## Conclusion

Network security is a critical component of overall system security. By securing network services, configuring firewalls, monitoring network activity, and using VPNs for secure remote access, you can significantly reduce the risk of external threats. In the next lecture, we will cover security tools and best practices to enhance the security of your Linux system further.