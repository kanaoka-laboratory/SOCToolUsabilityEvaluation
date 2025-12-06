# README


# Network Topology Overview

This document provides a detailed explanation of the network topology used in our usability evaluation of SOC tools.
The topology models a typical small-to-medium enterprise environment and includes a DMZ segment, an internal user network, and an internal server network.
The evaluated SOC tool (Prelude OSS) received logs generated according to this topology and the attack scenarios defined in the study.

## Network Diagram

![Network Topology](./network2.png)

---

## Topology Description

The network is divided into **three major segments**, each representing a common component of enterprise IT infrastructure:
(1) a perimeter/DMZ zone,
(2) an internal user network, and
(3) an internal server network.
A router and firewall coordinate traffic between these segments, enabling monitoring and log generation similar to a real operational environment.

---

## 1. External Connectivity

The organization connects to two external networks represented by the addresses **172.18.10.1** and **172.18.20.1**.
These external networks serve as potential attack sources during simulated scenarios, such as malware download or external command-and-control activity.

Traffic from outside flows into the enterprise through a **router (192.168.0.1)**, which forwards packets to the internal switching infrastructure.

---

## 2. L2 Switch A (192.168.0.2)

Switch A provides connectivity between the router, the firewall, and the lower internal network.
It essentially acts as the distribution switch linking the outside world to the internal infrastructure.
Traffic passing through this switch generates logs that are later consumed by the SIEM.

---

## 3. DMZ Segment (192.168.3.0/24)

A dedicated DMZ zone hosts public-facing servers that can be accessed from external networks:

* **DNS Server (192.168.3.1)**
* **Mail Server (192.168.3.2)**
* **Web Server (192.168.3.3)**

These servers are connected to the firewall via **192.168.3.254** and can be targets for reconnaissance or pivoting during simulated attacks.
Logs from these hosts contribute to analyzing early-stage attack indicators.

---

## 4. Firewall (192.168.3.254 / 192.168.1.254 / 192.168.2.254)

The firewall acts as the central control point that enforces network segmentation.
It connects three subnets:

* DMZ (192.168.3.0/24)
* Internal User Network (192.168.1.0/24)
* Internal Server Network (192.168.2.0/24)

It generates logs for:

* Access control decisions
* Administrative logins
* Configuration changes
* Allowed or blocked traffic flows

These logs are essential for evaluating whether the SOC tool can help analysts identify configuration tampering or suspicious access flow patterns.

---

## 5. Internal User Network (192.168.1.0/24)

This network represents typical end-user devices inside an enterprise.
It is connected through **L2 Switch B (192.168.1.1)** and contains:

* **WLAN Access Point (192.168.1.2)**
* **Laptops (P: .101, Q: .102, R: .103, S: .104)**
* **Desktops (X: .10, Y: .11, Z: .12)**

These devices generate logs related to:

* User authentication
* Internal lateral movement
* Abnormal access to servers
* Malware execution events

In the evaluation, compromised user machines were used as pivot points for simulated attacker actions.

---

## 6. Internal Server Network (192.168.2.0/24)

This segment contains key enterprise servers typically monitored by a SOC:

* **IDS (192.168.2.1)**
* **Active Directory (192.168.2.2)**
* **File Server (192.168.2.3)**
* **Application Server (192.168.2.4)**
* **Log Server (192.168.2.5)**
* **SIEM Server (192.168.2.6)**
* **DHCP Server (192.168.2.7)**
* **VPN Server (192.168.2.8)**

These systems generate high-value logs such as authentication events, file access, service usage, and anomaly alerts.
Simulated attack scenarios involved data access and exfiltration via the file server, along with IDS alerts triggered by reconnaissance activities.

---

## 7. Overall Characteristics

This network topology is designed to reflect:

* realistic enterprise segmentation (DMZ / users / servers)
* common IT operational components
* traffic flows that generate diverse log sources
* conditions under which Tier-1 SOC analysts typically work

By structuring the topology in this way, the evaluation environment supports:

* high-fidelity alert generation
* reproduction of common cyberattack chains
* appropriate contextual information for SOC usability testing

