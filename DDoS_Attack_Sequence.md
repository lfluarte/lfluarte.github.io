# SYN Flood Attack
```mermaid 
sequenceDiagram
participant Attacker
participant Botnet
participant WebServer
participant Firewall
Attacker->>+Botnet: Activate Malware
Botnet->>WebServer: Request Packets
WebServer->>Firewall: Waiting For Confirmation
rect rgb(66, 66, 245)
Firewall->>Botnet: Waiting for Final Handshake
Botnet-->>Firewall: No Answer
Firewall-->Botnet: Analyses IP address, and the traffic
Firewall->>Botnet: Blocks IP
end 
Botnet->>WebServer: Requests more packets
Attacker->>WebServer: Requests Packets
WebServer->>Firewall: Requests waiting for confirmation
Firewall->>Botnet: Waiting for Final Handshake
Botnet-->>Firewall: No Answer
Note Right of Firewall: Too many requests can't keep up.
Note Right of Firewall: Shuts Down
```
## Documentation
1. The attacker infects any IoT device with malware, creating bots and with many of them creating a botnet.
2. The botnet sends many handshake requests with spoofed IP's to the webserver where the firewall tries to finalize the handshake request.
3. Firewall then analyzes and recognizes faulty IP addresses then blocks the requests.
4. Botnet and Attacker repeatedly send more requests, overwhelming the firewall and causing the webserver to shut down. 
