# Case Study 1: Network Connectivity Troubleshooting

## Objective
Verify whether the Windows computer can communicate with its local network gateway and an external IP address.

## Tools Used
- Windows Command Prompt
- `ipconfig`
- `ping`

## Procedure

1. Ran `ipconfig` to identify the active network configuration.
2. Identified the default gateway.
3. Used `ping` to test communication with the gateway.
4. Used `ping 1.1.1.1` to test external IP connectivity.

## Findings

- The local gateway responded successfully.
- The external IP address responded successfully.
- Both tests reported zero packet loss.
- The external test showed relatively high average response time during the short test.

## Outcome

Local and external IP connectivity were working during testing. The results did not establish a persistent network latency issue.

## Skills Practised

- Basic network diagnostics
- IP configuration inspection
- Connectivity testing
- Interpreting ping results
- Technical documentation

## Evidence

Screenshots of the commands and results will be added after identifying and redacting any sensitive information.
