# Aegis Financial Network: Enterprise-Grade Infrastructure Modernization 🏦🌐

> **[EN]** A journey from legacy constraints to a modern, zero-trust network architecture.
>
> **[TR]** Geleneksel kısıtlamalardan modern, sıfır güvenli bir ağ mimarisine geçiş hikayesi.

---

## 🏗️ Technical Architecture & Branch Roles / Teknik Mimari ve Şube Rolleri

**[EN]** The network is designed across 4 strategic branches in Turkey, connected via OSPF Area 0 for seamless inter-city communication.
**[TR]** Ağ, Türkiye'deki 4 stratejik şube üzerine tasarlanmış olup, şehirlerarası kesintisiz iletişim için OSPF Area 0 üzerinden birbirine bağlanmıştır.

| City / Şehir | Role / Rol | IP Range / IP Aralığı |
| :--- | :--- | :--- |
| **Ankara (ANK)** | HQ & Main DC | $10.6.0.0/16$ |
| **Kayseri (KYSR)** | Commercial Ops | $10.38.0.0/16$ |
| **Yozgat (YZGT)** | Archive & Retail | $10.66.0.0/16$ |
| **Antalya (ANT)** | Disaster Recovery | $10.7.0.0/16$ |

---

## 🛠️ Detailed IP Planning / Detaylı IP Planlaması

**[EN]** Below is the mapping of critical endpoints across the infrastructure:
**[TR]** Altyapıdaki kritik uç noktaların eşleşmesi aşağıdadır:

* **Servers (VLAN 99):**
    * **ANK:** Server0 ($10.6.99.11/24$)
    * **KYSR:** Server1 ($10.38.99.11/24$)
    * **YZGT:** Server2 ($10.66.99.11/24$)
    * **ANT:** Server3 ($10.7.99.11/24$)
* **Departments / Departmanlar:**
    * **VLAN 10 (Engineering):** e.g., PC2 (ANK), PC4 (KYSR), PC10 (YZGT), PC12 (ANT)
    * **VLAN 20 (HR/Mgmt):** e.g., PC0 (ANK), PC6 (KYSR), PC8 (YZGT), PC14 (ANT)

---

## 🛡️ Security Policy (Zero Trust) / Güvenlik Politikası

**[EN]** Tiered Access Control Lists (ACLs) ensure that:
1.  Servers can replicate data between each other (Full Trust).
2.  PC-to-Server access is blocked at the source router for remote branches to prevent unauthorized lateral movement.

**[TR]** Katmanlı Erişim Kontrol Listeleri (ACL) şunları sağlar:
1.  Sunucular kendi aralarında veri replikasyonu yapabilir (Tam Güven).
2.  Yetkisiz yatay hareketi önlemek için, uzak şubelerdeki bilgisayarların sunuculara erişimi kaynak yönlendiricide engellenmiştir.

---

## 📊 Verification / Doğrulama

**[EN]** All security rules are verified through `show ip access-lists` match counters and Packet Tracer simulation modes.
**[TR]** Tüm güvenlik kuralları, `show ip access-lists` eşleşme sayaçları ve Packet Tracer simülasyon modları aracılığıyla doğrulanmıştır.

### Visual Proofs / Görsel Kanıtlar

| **The Problem (Legacy)** | **The Solution (Modern)** |
| :--- | :--- |
| **Legacy Failure:** Inter-VLAN failures due to SVI conflicts.<br>![Legacy Fail](docs/images/03_Legacy_Server_Ping_Fail.png) | **Modern Success:** Seamless server replication via ROAS.<br>![Modern Success](docs/images/07_Modern_Server_Ping_Success.png) |
| **Old Topology:**<br>![Legacy Topo](docs/images/01_Legacy_Topology_v1.png) | **Modern Topology:**<br>![Modern Topo](docs/images/04_Modern_Topology_v2.png) |

---

### **🚀 Project Status**
* **Migration:** Completed ✅
* **Security Audit:** Passed ✅
* **Documentation:** Bilingual (EN/TR) ✅