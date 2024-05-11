# Networking Basics and Advanced Configuration

This lecture provides an introduction to networking in Linux, from basic concepts to advanced network configurations. By the end of this session, you will understand how to manage network interfaces, configure settings, and troubleshoot common network issues.

## Introduction to Linux Networking

Linux networking involves managing network interfaces, connections, and data flow between systems over networks. Understanding the underlying principles and tools is crucial for effective network management.

### Key Networking Concepts

- **Network Interfaces**: These are the gateways through which a Linux system interacts with other systems on the network. Examples include Ethernet (e.g., eth0), WLAN (e.g., wlan0), and loopback (e.g., lo).
- **IP Addressing**: Every device on a network is assigned an IP address, which identifies it uniquely within the network. Linux supports both IPv4 and IPv6 addresses.
- **Routing**: Determines the path data takes from one system to another. Effective routing ensures data reaches its destination efficiently.

## Configuring Network Interfaces

Linux provides several tools for network configuration, with `ip` and `ifconfig` being the most commonly used.

### Using the `ip` command

The `ip` tool is versatile for network management. It is used to show and manipulate routing, devices, policy routing, and tunnels.

- **Viewing Network Interfaces**:
  ```bash
  ip link show       # Show all network interfaces and their status
  ```

- **Configuring IP Addresses**:
  ```bash
  ip addr add 192.168.1.100/24 dev eth0   # Assign IP address to eth0
  ip addr del 192.168.1.100/24 dev eth0   # Remove IP address from eth0
  ```

### Using the `ifconfig` command

Although deprecated and replaced by `ip` in most Linux systems, `ifconfig` is still widely used, particularly in older systems.

- **Viewing Network Configurations**:
  ```bash
  ifconfig           # Display all interfaces and their settings
  ```

- **Configuring Network Interfaces**:
  ```bash
  ifconfig eth0 up   # Activate eth0 interface
  ifconfig eth0 down # Deactivate eth0 interface
  ```

## Advanced Network Settings

Advanced network management involves fine-tuning settings for performance and security.

### Setting up Static Routes

Static routes can be configured to direct the traffic through a specified route instead of relying on routing algorithms.

- **Adding a Static Route**:
  ```bash
  ip route add 192.168.2.0/24 via 192.168.1.1 dev eth0
  ```

### Managing DNS Configurations

DNS settings are crucial for resolving domain names to IP addresses. These settings are typically configured in `/etc/resolv.conf`.

- **Editing DNS Settings**:
  ```bash
  echo "nameserver 8.8.8.8" > /etc/resolv.conf  # Set Google DNS as the DNS resolver
  ```

### Troubleshooting Network Issues

Effective troubleshooting is key to maintaining network reliability and performance.

- **Checking Connectivity**:
  ```bash
  ping google.com    # Check if google.com is reachable
  ```

- **Diagnosing Network Problems**:
  ```bash
  traceroute google.com  # Trace the path packets take to google.com
  ```

## Conclusion

This lecture has equipped you with the knowledge to manage and configure network interfaces in Linux, understand IP addressing, set static routes, manage DNS configurations, and troubleshoot common network issues. These foundational skills are essential for any system administrator or professional working with Linux networks.