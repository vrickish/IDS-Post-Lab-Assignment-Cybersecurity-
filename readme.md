## 1. Custom Rule 
I edited this file "`/etc/snort/rules/local.rules`" in my Kali virtual machine and this is what i inserted into it:
`alert icmp $EXTERNAL_NET any -> $HOME_NET 80 (msg:"[ALERT] ICMP PING ATTACK DETECTED"; itype:8; detection_filter: track by_src, count 20, seconds 1; sid:1000002; rev:1)`

## 2. The Attack Command:
![Screenshot From 2026-08-25 13-21-47](https://hackmd.io/_uploads/H1AOq-iDzl.png)

## 3. IDS Detection: A screenshort showing snort successfully triggering the ICMP alert
![Screenshot From 2026-08-25 13-22-10](https://hackmd.io/_uploads/BJPJjWivze.png)

## 4. Packet Capture: A screensot of Wireshark showing the flood of packets.
![Screenshot From 2026-08-25 13-26-34](https://hackmd.io/_uploads/BypGiZivGx.png)

## 5. Brief Analysis
The ICMP Flood (Ping Flood) is a type of Denial of Service (DDOS) attack, it operates at layer 3, which is the network layer. The ICMP flood works by blasting large volumes of ICMP echo request(type 8) at the target IP address and the Target system operating kernel tries to reply each of these request (type 0) and in doing so, it saturates the network bandwidth and consumes CPU processing power.
