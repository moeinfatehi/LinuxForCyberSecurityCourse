# Configuring and Securing Firewalls

This lecture explores the key concepts and practical implementations of firewalls in Linux. Understanding how to configure and manage firewalls is essential for securing network interfaces and controlling the flow of network traffic.

## Preparing Your Ubuntu System

Before configuring firewalls, ensure that you have the necessary tools installed on your Ubuntu system. Here are the installation steps for the primary firewall management utilities used in this lecture: `iptables`, `firewalld`, and `nftables`.

### Installing iptables

`iptables` is installed by default on most Linux distributions, including Ubuntu. If you need to install it or ensure it's up to date, you can use the following command:

```bash
sudo apt-get update
sudo apt-get install iptables
```

### Installing firewalld

`firewalld` is not installed by default on Ubuntu, but it can be easily installed via the package manager:

```bash
sudo apt-get update
sudo apt-get install firewalld
```

### Installing nftables

`nftables` is a newer tool that aims to replace `iptables`. It may not be pre-installed on older versions of Ubuntu:

```bash
sudo apt-get update
sudo apt-get install nftables
```

## Introduction to Firewalls

A firewall is a network security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules. In Linux, several tools can be used to configure and manage firewalls, providing robust defense mechanisms against network-based threats.

### Why Firewalls Are Important

- **Network Security**: Firewalls provide a barrier between a trusted internal network and untrusted external networks, such as the internet.
- **Traffic Management**: Firewalls can allow or block traffic based on IP addresses, port numbers, and protocols, controlling how the network is accessed.

## Using iptables

`iptables` is a traditional tool for configuring the Linux kernel's built-in firewall capabilities. It uses tables of rules to control packet filtering and routing.

### Basic iptables Commands

- **Viewing Rules**:
  ```bash
  sudo iptables -L  # List all active rules
  ```

- **Adding Rules**:
  ```bash
  sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT  # Allow SSH connections
  ```

- **Deleting Rules**:
  ```bash
  sudo iptables -D INPUT -p tcp --dport 22 -j ACCEPT  # Remove rule allowing SSH
  ```

### Saving and Restoring iptables Rules

Since `iptables` rules are not saved automatically after a reboot, it's important to save them manually.

- **Saving iptables Rules**:
  ```bash
  sudo iptables-save > /etc/iptables/rules.v4
  ```

- **Restoring iptables Rules**:
  ```bash
  sudo iptables-restore < /etc/iptables/rules.v4
  ```

## Firewalld

`firewalld` is a newer solution that provides a dynamic firewall management tool with support for network/firewall zones that define the trust level of network connections or interfaces.

### Working with Firewalld

- **Checking the Status**:
  ```bash
  sudo firewall-cmd --state
  ```

- **Adding and Removing Services**:
  ```bash
  sudo firewall-cmd --zone=public --add-service=http  # Allow HTTP traffic
  sudo firewall-cmd --zone=public --remove-service=http  # Block HTTP traffic
  ```

- **Permanent Changes**:
  ```bash
  sudo firewall-cmd --permanent --zone=public --add-service=https
  ```

## nftables

`nftables` is the successor to `iptables` and offers a simplified, consistent syntax and improved performance.

### Basic nftables Usage

- **Adding a Table and Chain**:
  ```bash
  sudo nft add table ip filter
  sudo nft add chain ip filter input { type filter hook input priority 0 \; }
  ```

- **Adding Rules**:
  ```bash
  sudo nft add rule ip filter input tcp dport 22 accept
  ```

## Practical Examples and Scenarios for Firewalling

### Scenario 1: Securing a Web Server

- **Objective**: Allow only HTTP and HTTPS traffic to your server, while blocking all other ports to minimize the attack surface.

- **Using iptables**:
  ```bash
  # Allow HTTP
  sudo iptables -A INPUT -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
  # Allow HTTPS
  sudo iptables -A INPUT -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
  # Drop all other inbound traffic
  sudo iptables -A INPUT -j DROP
  ```

- **Using firewalld**:
  ```bash
  # Set default zone to drop
  sudo firewall-cmd --set-default-zone=drop
  # Allow HTTP and HTTPS in the public zone
  sudo firewall-cmd --zone=public --add-service=http
  sudo firewall-cmd --zone=public --add-service=https
  sudo firewall-cmd --runtime-to-permanent
  ```

### Scenario 2: Protecting SSH Access

- **Objective**: Allow SSH access only from a specific network subnet, enhancing the security of remote access.

- **Using iptables**:
  ```bash
  # Allow SSH only from 192.168.1.0/24 subnet
  sudo iptables -A INPUT -p tcp --dport 22 -s 192.168.1.0/24 -j ACCEPT
  # Drop all other SSH traffic
  sudo iptables -A INPUT -p tcp --dport 22 -j DROP
  ```

- **Using firewalld**:
  ```bash
  # Create a new zone for secure SSH
  sudo firewall-cmd --new-zone=secure_ssh --permanent
  # Reload to apply changes
  sudo firewall-cmd --reload
  # Add SSH service and source IP range to the zone
  sudo firewall-cmd --zone=secure_ssh --add-service=ssh
  sudo firewall-cmd --zone=secure_ssh --add-source=192.168.1.0/24
  # Apply permanently
  sudo firewall-cmd --runtime-to-permanent
  ```

### Scenario 3: Preventing DDoS Attacks

- **Objective**: Implement rate limiting on incoming requests to prevent DDoS attacks.

- **Using iptables**:
  ```bash
  # Limit new TCP connections to 30 per minute
  sudo iptables -A INPUT -p tcp -m state --state NEW -m limit --limit 30/minute --limit-burst 10 -j ACCEPT
  sudo iptables -A INPUT -p tcp -m state --state NEW -j DROP
  ```

- **Using nftables**:
  ```bash
  # Create a rule for rate limiting
  sudo nft add rule ip filter input ip protocol tcp tcp flags & (fin | syn) == syn limit rate over 30/minute burst 5 packets drop
  ```

## Conclusion

Configuring and managing firewalls in Linux requires a good understanding of the available tools and the scenarios they best suit. `iptables`, `firewalld`, and `nftables` provide powerful and flexible options for securing your Linux systems against unauthorized network traffic. Mastery of these tools is crucial for any network administrator or cybersecurity professional.