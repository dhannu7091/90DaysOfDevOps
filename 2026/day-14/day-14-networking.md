# Day 14 – Networking Fundamentals & Hands-on Checks

## Quick Concepts (write 1–2 bullets each)
1. OSI layers (L1–L7) vs TCP/IP stack (Link, Internet, Transport, Application)
- OSI layer (L1-L7) is a conceptual model.
- TCP/IP has 4 layers (Link, internet, transport, application). it is pratical model used in real networking.
2. Where IP, TCP/UDP, HTTP/HTTPS, DNS sit in the stack
  - IP -> internet layer
  - TCP/UDP -> transport layer
  - HTTP/HTTPS -> application layer
  - DNS -> application layer
3. One real example: “`curl https://example.com` = App layer over TCP over IP”
- Output of `curl https://google.com`:
  ```
  ubuntu@ip-172-31-17-47:~$ curl https://google.com
  <HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
  <TITLE>301 Moved</TITLE></HEAD><BODY>
  <H1>301 Moved</H1>
  The document has moved
  <A HREF="https://www.google.com/">here</A>.
  </BODY></HTML>
  ```
---
## Hands-on Checklist (run these; add 1–2 line observations)
1. Identity: `hostname -I` (or `ip addr` show) — note your IP.
   - My ip address is  `172.31.17.47`
2. Reachability: `ping <target>` — mention latency and packet loss.
   - Avg latency 1.23ms, 0 packet loss
     ```
      --- google.com ping statistics ---
      142 packets transmitted, 142 received, 0% packet loss, time 141196ms
      rtt min/avg/max/mdev = 1.205/1.237/1.506/0.034 ms
      ```
3. Path: `traceroute <target>` (or `tracepath`) — note any long hops/timeouts.
   - First hope is router (240.1.192.14). no timeouts.
4. Ports: `ss -tulpn` (or `netstat -tulpn`) — list one listening service and its port.
   - Here is service and its port:
     ```
     Netid            State             Recv-Q            Send-Q                           Local Address:Port
     tcp              LISTEN            0                 511                                    0.0.0.0:80
     ```
5. Name resolution: `dig <domain>` or `nslookup <domain>` — record the resolved IP.
   - Here is resolved ip:
     ```
     trainwithshubham.com.	300	IN	A	15.197.225.128
     trainwithshubham.com.	300	IN	A	3.33.251.168
     ```
6. HTTP check: `curl -I <http/https-url>` — note the HTTP status code.
   - Recevied HTTP/2 301 -> redirect (google.com)
   - Recevied HTTP/1.1 405 Method Not Allowed  (trainwithshubham.com)
7. Connections snapshot: `netstat -an | head` — count ESTABLISHED vs LISTEN (rough).
   - 1 ESTABLISHED,  6 LISTEN

Pick one target service/host (e.g., google.com, your lab server, or a local service) and stick to it for ping/traceroute/curl where possible.

---
## Mini Task: Port Probe & Interpret
1. Identify one listening port from `ss -tulpn` (e.g., SSH on 22 or a local web app).
   - NGINX on 80
   - SSH on 22
     ```
     Netid            State             Recv-Q            Send-Q                           Local Address:Port
     tcp              LISTEN            0                 511                                    0.0.0.0:80   
     tcp              LISTEN            0                 4096                                   0.0.0.0:22
     ```
2. From the same machine, test it: `nc -zv localhost <port>` (or `curl -I http://localhost:<port>`).
   - Port 80 reachable, nginx is running
3. Write one line: is it reachable? If not, what’s the next check? (e.g., service status, firewall).
   - service status `systemctl status nginx`

---
## Reflection (add to your markdown)
1. Which command gives you the fastest signal when something is broken?
   - `ping` - network level issue
   - `curl -I` - application issue
2. What layer (OSI/TCP-IP) would you inspect next if DNS fails? If HTTP 500 shows up?
   - DNS - Application layer  `dig` output
3. Two follow-up checks you’d run in a real incident.
   - Network `ping` 
   - Service status `systemctl status <service>`







