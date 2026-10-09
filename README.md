# Windows IT Support Troubleshooting Lab

## Project Overview

This project documents hands-on Windows IT support exercises focused on network connectivity, DNS resolution, network adapter configuration, and system resource inspection.

Using built-in Windows diagnostic tools, I practised investigating connectivity issues, analysing command-line output, comparing network behaviour, and verifying results through repeat testing.

The project demonstrates a structured troubleshooting approach: gathering evidence, investigating possible causes, testing connectivity, and documenting findings accurately.

## Objectives

- Diagnose basic network connectivity.
- Investigate inconsistent DNS responses and intermittent timeouts.
- Inspect network adapter and IP configuration.
- Review system information and running processes.
- Verify connectivity after diagnostic testing.
- Document findings and identify when further investigation is required.

## Tools and Technologies

- Windows Command Prompt (CMD)
- `ipconfig`
- `ping`
- `nslookup`
- `netsh`
- `systeminfo`
- `tasklist`
- `curl`

## Lab Environment

- **Operating System:** Windows
- **Network Connections:** Wi-Fi and mobile hotspot
- **DNS Resolvers Tested:** Router DNS, Cloudflare DNS (1.1.1.1), and Google Public DNS (8.8.8.8)
- **Approach:** Command-line diagnostics and verification testing

## Task 1: Network Connectivity Troubleshooting

### Objective
Verify connectivity between the computer, the local network gateway, and an external IP address.

### Commands Used

```cmd
ipconfig
ping <default-gateway>
ping 1.1.1.1
```

### Findings

- Identified the active network adapter's IPv4 configuration.
- Received successful responses from the local gateway.
- Received successful responses from an external IP address.
- Observed relatively high average response times during a short external connectivity test.

### Outcome

Local and external IP connectivity were working during testing. The short test did not establish a persistent latency problem.

## Task 2: DNS Resolution Troubleshooting

### Objective
Investigate inconsistent DNS responses, intermittent timeouts, and unexpected domain-name results.

### Commands Used

```cmd
ipconfig /all
nslookup www.google.com
nslookup www.microsoft.com
nslookup -type=A www.google.com 1.1.1.1
nslookup -type=A www.microsoft.com 1.1.1.1
nslookup -type=A www.google.com 8.8.8.8
nslookup -type=A www.microsoft.com 8.8.8.8
curl -I https://www.google.com
```

### Investigation

1. Inspected the active Wi-Fi configuration and identified the router as the configured DNS server.
2. Queried Google and Microsoft domain names through Cloudflare DNS and Google Public DNS.
3. Observed initial responses containing unexpected `.com.ng` domain variants and occasional DNS timeouts.
4. Repeated the DNS tests using a mobile hotspot, where the expected domain names were returned.
5. Reconnected to the original Wi-Fi and repeated the tests using the router's DNS resolver and Cloudflare DNS.
6. Performed final verification using DNS queries and an HTTPS request.

### Verification Results

- Cloudflare DNS returned the expected `www.google.com` domain and IPv4 records.
- The router's DNS resolver returned expected domain results for Google and Microsoft.
- An HTTPS request to Google returned `HTTP/1.1 200 OK`.

### Outcome

DNS resolution and HTTPS connectivity were working during final verification. The earlier inconsistent responses were no longer reproducible in the final tests, but the root cause was not established. No specific corrective change was confirmed.

### Skills Demonstrated

DNS diagnostics, resolver comparison, network troubleshooting, repeat testing, and evidence-based documentation.

## Task 3: Network Adapter and IP Configuration

### Objective
Inspect the active Wi-Fi connection and verify its network configuration.

### Commands Used

```cmd
ipconfig /all
netsh wlan show interfaces
```

### Findings

- Confirmed that the Wi-Fi adapter was connected.
- Reviewed the IPv4 address, subnet mask, default gateway, DHCP status, and DNS server.
- Inspected wireless signal strength, channel, and connection rates.
- Identified virtual network adapters associated with virtualisation tools.

### Outcome

The active Wi-Fi adapter had a valid-looking IP configuration and was connected during inspection. No obvious adapter disconnection or IP configuration fault was identified.

## Task 4: Windows System and Process Inspection

### Objective
Review system specifications, available memory, and running processes as an initial system-health check.

### Commands Used

```cmd
systeminfo
tasklist
```

### Findings

- Inspected operating system and hardware information.
- Reviewed physical memory and available memory at the time of the check.
- Identified running processes, including Windows security services and installed lab tools.
- Recognised that a process list alone does not establish whether a computer has a performance problem.

### Outcome

Established a basic system and process inventory. No performance fault was confirmed because CPU utilisation, performance trends, and a specific user-reported symptom were not assessed.

## Troubleshooting Methodology

I followed a structured process throughout the lab:

1. **Identify:** Establish the symptoms or diagnostic question.
2. **Collect evidence:** Run appropriate Windows diagnostic commands.
3. **Analyse:** Compare outputs and identify unexpected results.
4. **Investigate:** Perform additional tests to narrow down possible causes.
5. **Verify:** Repeat relevant tests to check whether expected behaviour is present.
6. **Document:** Record findings and limitations without assuming an unverified root cause.

## Key Skills Practised

- Windows IT support fundamentals
- Network connectivity troubleshooting
- DNS resolution analysis
- TCP/IP configuration inspection
- Command-line diagnostics
- System and process inspection
- HTTPS connectivity verification
- Technical documentation
- Evidence-based problem analysis

## Limitations and Further Investigation

This was a personal troubleshooting lab, not a record of confirmed resolutions to real user incidents.

The DNS investigation showed inconsistent responses that were no longer reproducible during final verification. However, the underlying cause was not confirmed. If the behaviour recurs, further investigation could include reviewing router DNS settings, repeating resolver comparisons, and checking relevant router or network-provider configuration.

The system inspection was a baseline review rather than a complete performance diagnosis. Further testing would require examining CPU and memory utilisation over time and investigating a specific reported symptom.

## Conclusion

This lab provided practical experience using built-in Windows tools to investigate network connectivity, DNS resolution, adapter configuration, and system processes.

It strengthened my ability to collect diagnostic evidence, compare test results, verify connectivity, and document technical findings while recognising when further investigation is required.

**Project Type:** Personal IT Support Troubleshooting Lab  
**Environment:** Windows  
**Focus:** Technical support, networking fundamentals, and structured troubleshooting

## Privacy Note

Before publishing screenshots or command outputs, remove computer names, usernames, MAC addresses, serial numbers, Wi-Fi network names, public IP addresses, and other identifying information where appropriate.
