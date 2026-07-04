# Part 1 – Finding Hosts on a Network

## What We Want to Do

We need to find out which hosts are active on a network. We will use Nmap and ARP scanning to do this before we do a scan of the network.

---

# What is Finding Hosts?

Finding hosts is the step in scanning a network. It helps us figure out which systems are online. Then we can scan those hosts.

---

## 1. Find Live Hosts Using ARP Scan

### What We Are Doing

We want to find all the devices that are connected to our network.

### What to Type

```bash

sudo arp-scan --localnet

```

### How It Works

This uses ARP requests to find devices on our LAN.

> If you need to install it:

```bash

sudo apt install -scan

```

### Picture

![Alt text](screenshots/arp-scan-localnet.png)

---

## 2. Find Live Hosts Using Nmap

### What We Are Doing

We want to find hosts on our subnet without checking their ports.

### What to Type

```bash

sudo nmap -sn 192.168.1.0/24

```

### How It Works

This does a host discovery only it does not scan ports.

Replace the subnet with your network.

### Picture

![Alt text](screenshots/nmap-sn-network.png)

---

## 3. Scan One Host

### What We Are Doing

We want to check if a specific host's online.

### What to Type

```bash

nmap -sn 192.168.1.10

```

### How It Works

This checks if one target system is reachable.

Replace the IP address with a host on your network.

### Picture

![Alt text](screenshots/sn-single-host.png)

---

## 4. Save the Scan Results

### What We Are Doing

We want to save the host discovery results so we can look at them later.

### What to Type

```bash

nmap -sn 192.168.1.0/24 -oN host-discovery.txt

```

### How It Works

This saves the output in a normal text file.

### Picture

![Alt text](screenshots/nmap-save-output.png)

---

## 5. Look at the Saved Report

### What We Are Doing

We want to open the saved scan report.

### What to Type

```bash

cat host-discovery.txt

```

### How It Works

This shows us what is in the saved Nmap report.

### Picture

![Alt text](screenshots/view-host-discovery-report.png)

---

# Things We Learned

- Finding hosts, on a network

- ARP scanning

- Using Nmap to find hosts

- Finding live hosts

- Saving Nmap output

---

# conclusion

In this part I learned how to:

- Find hosts using ARP.

- Use Nmap to find hosts.

- Scan one host.

- Save scan results.

- Look at reports.


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Part 2 – Port Scanning

## Objective

I want to learn how to find open closed and filtered ports using Nmap scan methods.

## What is Port Scanning?

Port scanning is checking which network ports on a target system are open and what services are available through them.

When I see ports it means there are services running that might need more assessment.

## 1. TCP SYN Scan

### Scenario

I will do a stealth TCP SYN scan.

### Command

```bash

sudo nmap -sS 192.168.1.10

```

### Description

This scan does a SYN scan without finishing the TCP handshake.

It is a way to see which ports are open.

### Screenshot

![Alt text](screenshots/nmap-syn-scan.png)

## 2. TCP Connect Scan

### Scenario

I need to do a full TCP connection scan.

### Command

```bash

nmap -sT 192.168.1.10

```

### Description

This scan uses the operating systems TCP stack to make a connection.

It is slower than a SYN scan. Gets more information.

### Screenshot

![Alt text](screenshots/connect-scan.png)

## 3. UDP Scan

### Scenario

I want to find UDP ports.

### Command

```bash

sudo nmap -sU 192.168.1.10

```

### Description

This scan looks for UDP services running on the target.

UDP scans are slower and less reliable than scans.

### Screenshot

![Alt text](screenshots/nmap-udp-scan.png)

## 4. Scan Specific Ports

### Scenario

I will scan some ports.

### Command

```bash

nmap -p 22,80,443 192.168.1.10

```

### Description

This scan only looks at the ports I specify.

It is useful when I only care about services.

### Screenshot

![Alt text](screenshots/specific-ports.png)

## 5. Scan All TCP Ports

### Scenario

I need to scan all ports.

### Command

```bash

sudo nmap -p- 192.168.1.10

```

### Description

This scan looks at 65,535 TCP ports.

It takes a time and might be noisy.

### Screenshot

![Alt text](screenshots/nmap-ports.png)

## Key Concepts Learned

- TCP SYN Scan

- TCP Connect Scan

- UDP Scan

- Port Selection

- Full Port Scanning


# Conclusion

In this part, I learned:

- Different types of Nmap port scans.
- The difference between TCP and UDP scanning.
- How to scan selected ports.
- How to scan all TCP ports.
