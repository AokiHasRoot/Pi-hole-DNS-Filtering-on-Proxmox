# Pi-hole-DNS-Filtering-on-Proxmox
Deployed Pi-hole in a Proxmox VE LXC container for DNS-based ad blocking. Configured upstream DNS, connected a Windows PC, and tested domain resolution and blocking with nslookup. Troubleshot gateway connectivity issues while developing hands-on skills in Linux, virtualization, IPv4 networking, and cybersecurity.

## Project Overview

I deployed **Pi-hole**, a network-level DNS sinkhole, inside a Linux container on **Proxmox VE**. The goal was to gain hands-on experience with virtualization, Linux administration, DNS configuration, network troubleshooting, and DNS-based ad and tracking domain blocking.

This project is part of my ongoing IT and cybersecurity homelab.

## Lab Environment

| Component | Configuration |
|---|---|
| Hypervisor | Proxmox VE |
| DNS filtering service | Pi-hole |
| Deployment method | Linux LXC container |
| Pi-hole IP address | `192.0.2.50` |
| Default gateway | `192.0.2.1` |
| Upstream DNS provider | Google DNS |
| Test client | Windows workstation |
| Management interface | Pi-hole web dashboard |

*Privacy note: IP addresses shown in this README are documentation examples and do not represent the actual lab configuration. Real network details and credentials have been omitted.*

## Implementation

1. Created and configured a Linux container in Proxmox VE.
2. Troubleshot network connectivity caused by an incorrectly configured default gateway.
3. Corrected the gateway configuration and verified connectivity.
4. Installed Pi-hole and configured its upstream DNS provider.
5. Accessed the Pi-hole administration dashboard.
6. Configured a Windows workstation to use Pi-hole for DNS resolution.
7. Tested normal DNS resolution and DNS-based domain blocking from Windows Command Prompt.

## Validation and Testing

### Test 1: Normal DNS Resolution

Command:

```powershell
nslookup example.com
```

Result: The DNS response identified Pi-hole as the DNS server and returned IP addresses for `example.com`.

**What this verified:** The Windows workstation was sending DNS queries to Pi-hole and receiving valid responses for an allowed domain.

### Test 2: Blocked-Domain Response

Command:

```powershell
nslookup doubleclick.net
```

Result: Pi-hole returned `0.0.0.0` and `::`, consistent with a blocked-domain response.

**What this verified:** Pi-hole was applying its DNS filtering policy to the test domain.

## Troubleshooting Experience

During deployment, I encountered a network connectivity issue caused by an incorrectly configured default gateway.

Troubleshooting steps:

- Identified an incorrect gateway address in the container configuration.
- Corrected the gateway to match the lab's network configuration.
- Retested network connectivity.
- Continued the installation after connectivity was restored.
- Verified DNS resolution from a Windows client.
- Tested DNS filtering using a known advertising domain.

This troubleshooting process provided practical experience with IPv4 networking, default gateways, DNS resolution, and client-server connectivity.

## Skills Practiced

- Proxmox VE virtualization
- Linux system administration
- LXC container deployment
- DNS resolution and upstream DNS configuration
- IPv4 addressing and default gateways
- Windows network configuration
- Command-line troubleshooting
- DNS-based advertising and tracking domain blocking
- Service validation and technical documentation
- Cybersecurity homelab development

## Future Improvements

- Extend Pi-hole DNS filtering to additional devices.
- Plan and implement network-wide DNS configuration.
- Prevent IP address conflicts through appropriate DHCP planning.
- Investigate IPv6 DNS behavior and potential DNS bypass paths.
- Review Pi-hole Query Log and blocking statistics.
- Create a sanitized network topology diagram.
- Add screenshots of the dashboard and test results with identifying details removed.
- Document future configuration changes and troubleshooting findings.

## Project Status

**Initial deployment and Windows client testing completed.**

Future work includes expanding DNS filtering to additional devices, improving network-wide DNS management, investigating IPv6 behavior, and documenting the completed configuration.

---

*This project demonstrates hands-on practice with virtualization, Linux administration, networking, DNS filtering, and troubleshooting as part of my continued development in IT and cybersecurity.*
