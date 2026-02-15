# Aegis Financial Network: Enterprise-Grade Infrastructure Modernization 🏦🌐

> **[EN]** A journey from legacy constraints to a modern, zero-trust network architecture. Designed with OSPF, LACP, and Tiered ACLs.
>
> **[TR]** Geleneksel kısıtlamalardan modern, sıfır güvenli bir ağ mimarisine geçiş hikayesi. OSPF, LACP ve Katmanlı ACL'ler ile tasarlandı.

![Modern Topology](docs/images/04_Modern_Topology_v2.png)
*Figure 1: The Final Enterprise Architecture (Router-on-a-Stick & OSPF Backbone)*

---

## 🚀 Project Overview / Proje Özeti

**[EN]** This project demonstrates the migration of a multi-branch financial network from a **Legacy Layer 3 Switching** model to a robust **Router-on-a-Stick (ROAS)** architecture. The primary goal was to resolve inter-VLAN routing conflicts, centralize security policies, and ensure high availability across 4 major cities in Turkey.

**[TR]** Bu proje, çok şubeli bir finans ağının **Eski Layer 3 Switching** modelinden, güçlü bir **Router-on-a-Stick (ROAS)** mimarisine geçişini gösterir. Temel amaç; VLAN'lar arası yönlendirme çakışmalarını çözmek, güvenlik politikalarını merkezileştirmek ve Türkiye'nin 4 büyük şehri arasında yüksek erişilebilirlik sağlamaktır.

---

## ⚔️ The Transformation: Before vs. After / Dönüşüm: Önce ve Sonra

### 1. Architecture & Reliability / Mimari ve Güvenilirlik

| **Legacy Failure (L3 Switching)** | **Modern Success (ROAS)** |
| :--- | :--- |
| **Problem:** SVI-based routing caused Access List conflicts, blocking critical Server-to-Server replication.<br>*(SVI tabanlı yönlendirme ACL çakışmalarına ve sunucu replikasyon hatalarına yol açtı.)* | **Solution:** Centralized routing on Cisco 2911 Routers restored full connectivity for VLAN 99 (Servers).<br>*(Yönlendirmenin Router'larda toplanması sunucu iletişimini kurtardı.)* |
| ![Legacy Fail](docs/images/03_Legacy_Server_Ping_Fail.png) | ![Modern Success](docs/images/07_Modern_Server_Ping_Success.png) |

---

## 🛡️ Security Architecture (Zero Trust) / Güvenlik Mimarisi

**[EN]** A "Zero Trust" policy is implemented using Extended ACLs on the Router sub-interfaces.
**[TR]** Router alt arayüzlerinde Genişletilmiş ACL'ler kullanılarak "Sıfır Güven" politikası uygulanmıştır.

### 🔒 Access Control Logic
1.  **VLAN 99 (Servers):** Isolated from unauthorized PC access but open for internal replication.
2.  **VLAN 10/20 (Users):** Strictly segmented. Engineering (VLAN 10) cannot access HR (VLAN 20).
3.  **Geo-Blocking:** Remote branches cannot access the Data Center unless authorized.

### 📸 Security Verification / Güvenlik Kanıtları

| **Access Denied (Proof)** | **ACL Logs (Matches)** |
| :--- | :--- |
| Unauthorized PC pinging a remote server is **blocked** instantly.<br>*(Yetkisiz PC'nin uzak sunucuya erişimi anında engelleniyor.)* | `show ip access-lists` command confirms the dropped packets.<br>*(`matches` sayacı engellenen paketleri doğruluyor.)* |
| ![Access Denied](docs/images/08_Modern_PC_Access_Denied.png) | ![ACL Proof](docs/images/06_Modern_ACL_Security_Proof.png) |

---

## ⚡ High Availability & Redundancy / Yüksek Erişilebilirlik

**[EN]** To prevent single points of failure, **LACP (Link Aggregation Control Protocol)** is configured between Access and Distribution layers, providing 200 Mbps bandwidth.
**[TR]** Tekil hata noktalarını önlemek için, Erişim ve Dağıtım katmanları arasında **LACP** yapılandırılarak 200 Mbps bant genişliği sağlanmıştır.

![EtherChannel Proof](docs/images/05_Modern_EtherChannel_v2.png)
*Figure 2: Active EtherChannel Bundling (LACP Mode)*

---

## 🏗️ Technical Details & IP Scheme / Teknik Detaylar

**Protocol Stack:**
* **Routing:** OSPF Area 0 (Backbone)
* **Encapsulation:** 802.1Q (Dot1Q)
* **Redundancy:** LACP (802.3ad) / PVST+

| Location | Role | Subnet | VLANs |
| :--- | :--- | :--- | :--- |
| **Ankara** | HQ / Main DC | $10.6.0.0/16$ | 10, 20, 99 |
| **Kayseri** | Operations | $10.38.0.0/16$ | 10, 20, 99 |
| **Yozgat** | Archive | $10.66.0.0/16$ | 10, 20, 99 |
| **Antalya** | Disaster Recovery | $10.7.0.0/16$ | 10, 20, 99 |

---

## 📂 Repository Structure / Klasör Yapısı

* `v1_legacy/`: Contains the initial failed architecture files. *(Hatalı başlangıç mimarisi)*
    * *Reference Image:* `01_Legacy_Topology_v1.png`
* `v2_modern/`: Contains the final production-ready configuration. *(Final prodüksiyon mimarisi)*
    * *Reference Image:* `04_Modern_Topology_v2.png`
* `docs/images/`: Evidence screenshots (Pings, ACLs, Show commands).

---

### 👨‍💻 About the Engineer
Designed by **Yunus Emre Gümüş**, Computer Engineering Senior Student.
*Focus: Network Security, Cloud Architecture, and Enterprise Infrastructure.*