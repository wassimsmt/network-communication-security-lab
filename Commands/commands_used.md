Environment:
- Kali Linux (Attacker)
- Ubuntu Server (Target)
- VirtualBox Host-Only Network

---

# Commands Used – Network Communication & Security Lab

---

## 1️⃣ Network Verification (Both VMs)

### Check IP addresses
ip a

### Check routing table
ip route

### Test connectivity (from Kali to Ubuntu)
ping -c 4 <UBUNTU_HOSTONLY_IP>

---

## 2️⃣ Service Installation (Ubuntu Target)

### Update system
sudo apt update

### Install required services and tools
sudo apt install -y openssh-server nginx ufw tcpdump net-tools

### Check service status
sudo systemctl status ssh --no-pager
sudo systemctl status nginx --no-pager

---

## 3️⃣ Web Server Validation (Ubuntu)

### Create test webpage
echo "Network Communication & Security Lab - Wassim" | sudo tee /var/www/html/index.html

### Test locally
curl -I http://localhost

---

## 4️⃣ Identify Listening Services (Ubuntu)

### Show listening TCP/UDP ports
sudo ss -tulpn

---

## 5️⃣ Baseline Scanning (Kali – Before Firewall)

### Full TCP SYN scan
sudo nmap -sS -sV -O -p- <UBUNTU_HOSTONLY_IP>

### UDP scan (top common ports)
sudo nmap -sU --top-ports 50 <UBUNTU_HOSTONLY_IP>

### Test HTTP service manually
curl http://<UBUNTU_HOSTONLY_IP>

### Test SSH port manually
nc -vz <UBUNTU_HOSTONLY_IP> 22

---

## 6️⃣ Packet Capture (Ubuntu – tcpdump)

### Identify correct interface
ip a

### Capture HTTP traffic
sudo tcpdump -i <HOSTONLY_INTERFACE> -nn host <KALI_HOSTONLY_IP>

### Capture SSH traffic
sudo tcpdump -i <HOSTONLY_INTERFACE> -nn host <KALI_HOSTONLY_IP> and tcp port 22

---

## 7️⃣ Firewall Hardening (Ubuntu – UFW)

### Disable and reset firewall
sudo ufw disable
sudo ufw reset

### Set default policies
sudo ufw default deny incoming
sudo ufw default allow outgoing

### Allow required services
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp

### Enable firewall
sudo ufw enable

### Verify firewall status
sudo ufw status verbose

---

## 8️⃣ Verification Scans (Kali – After Firewall)

### TCP scan after firewall changes
sudo nmap -sS -sV -p 1-1000 <UBUNTU_HOSTONLY_IP>

### UDP scan after firewall changes
sudo nmap -sU --top-ports 50 <UBUNTU_HOSTONLY_IP>

### Test blocked port
nc -vz <UBUNTU_HOSTONLY_IP> 443

---

## 9️⃣ Firewall Logging (Ubuntu)

### Enable logging
sudo ufw logging on

### View recent firewall logs
sudo tail -n 50 /var/log/ufw.log

---

## 🔟 Saving Scan Outputs to File (Optional – For Repo Artifacts)

### Save TCP scan to file
sudo nmap -sS -sV <UBUNTU_HOSTONLY_IP> -oN nmap_tcp_before.txt

### Save UDP scan to file
sudo nmap -sU --top-ports 50 <UBUNTU_HOSTONLY_IP> -oN nmap_udp_before.txt

### Save tcpdump output
sudo tcpdump -i <HOSTONLY_INTERFACE> -nn host <KALI_HOSTONLY_IP> > tcpdump_capture.txt
