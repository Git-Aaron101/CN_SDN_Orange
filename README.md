# 📡 Broadcast Traffic Control using SDN

**Author:** Aaron Sijo  
**SRN:** PES2UG24CS012

## 🧠 Project Description
This project implements **broadcast traffic control in a network using Software Defined Networking (SDN)**.

Using a Ryu controller and Mininet, the system:
- Detects broadcast and multicast packets  
- Monitors their frequency  
- Limits excessive broadcast traffic  
- Installs flow rules for efficient forwarding  

This helps prevent **network congestion and broadcast storms** while maintaining normal communication.

---

## ⚙️ Technologies Used
- Mininet  
- Ryu Controller  
- OpenFlow 1.3  
- Python  

---

## 🧪 Features Implemented
- Broadcast packet detection  
- Traffic monitoring and logging  
- Threshold-based broadcast filtering  
- Learning switch behavior  
- Flow rule installation  
- Performance evaluation (Latency & Throughput)

---

## 📸 Screenshots

### 🔹 Broadcast Detection (Initial)
![BroadcastT1](CNOrngSSs/BroadcastT1.png)

---

### 🔹 Broadcast Control (Threshold Applied)
![BroadcastT2](CNOrngSSs/BroadcastT2.png)

---

### 🔹 Flow Rule Installation
![Flowcontrol](CNOrngSSs/Flowcontrol.png)

---

### 🔹 Latency Measurement
![Latency](CNOrngSSs/Latency.png)

---

### 🔹 Connectivity Check
![Pingall](CNOrngSSs/Pingall.png)

---

### 🔹 Throughput Measurement
![Throughput](CNOrngSSs/Throughput.png)

---

## 🚀 Commands

ryu-manager broadcast_control.py
### Clean previous setup
sudo mn -c

### Start Mininet
sudo mn --topo single,3 \
--controller=remote,ip=127.0.0.1,port=6653 \
--switch ovsk,protocols=OpenFlow13

### Show topology
net

### Test connectivity
pingall

### Measure latency
h1 ping -c 4 h2

### View flow rules
sh ovs-ofctl -O OpenFlow13 dump-flows s1

### Generate broadcast traffic
h1 arping -I h1-eth0 10.0.0.2

### Measure throughput
h1 iperf -s &
sleep 2
h2 iperf -c 10.0.0.1

### Optional broadcast stress
h1 ping -b 10.0.0.255

### Exit
exit
