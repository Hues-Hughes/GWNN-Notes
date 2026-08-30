# 🎤 Team 6 Teachback Presentation
## Secure Access, WAN Connectivity & Cloud Security Controls
### CompTIA Security+ SY0-701 | Lesson 187.6 | Doc ID: Team6_Teachback_187-6

---

## 📌 Slide 1 — Title & Scope

**Title:** Secure Access, WAN Connectivity & Cloud Security Controls

**Team 6 | CompTIA Security+ SY0-701 Aligned**

> *"The perimeter is dead. Security now lives in the cloud."*

**What we're covering today:**
- Cloud data protection & automated patching
- SD-WAN architecture
- SASE — pronounced **"sassy"** *(Secure Access Service Edge)*
- Real-world remote work scenario
- One exam-style practice question

---

## 📌 Slide 2 — Learning Objectives

By the end of this teachback, you'll be able to:

1. ✅ Analyze cloud security design considerations — data protection, DLP, and automated patching
2. ✅ Explain **SD-WAN** architecture and encrypted overlay routing
3. ✅ Explain **SASE** and how it converges networking + security
4. ✅ Compare traditional VPN backhauling vs. cloud-delivered SASE PoPs

---

## 📌 Slide 3 — Cloud Data Protection & Automated Patching

### 🔐 Cloud Data Protection
From the Lesson 187.6 responsibility matrix, **customers own:**
- Encryption at rest and in transit
- Data Loss Prevention (DLP) configuration
- Access logging across cloud pipelines
- Encryption key management

> ⚠️ The cloud provider secures the *infrastructure* — **you** secure the *data*.

### 🔧 Automated Patching
- Cloud-native patch managers (e.g., AWS Systems Manager Patch Manager, Azure Update Manager) automate guest OS and instance updates
- Reduces the window of vulnerability between patch release and deployment
- Ties directly into **IaC (Infrastructure as Code)** pipelines — automated, consistent, auditable

> 💡 **Key Point:** Unpatched cloud instances are one of the top attack vectors. Automation closes that gap without manual intervention.

---

## 📌 Slide 4 — SD-WAN Explained

### What is SD-WAN?
**Software-Defined Wide Area Network** — an overlay network that uses commodity internet links with **centralized policy enforcement and encryption**.

Built on the **SDN (Software Defined Networking)** model from Lesson 187.6:

| Plane | Function |
|---|---|
| **Control Plane** | Decides how traffic is prioritized, secured, and routed |
| **Data Plane** | Switches/routes traffic and enforces access controls |
| **Management Plane** | Monitors traffic conditions and network status |

**SD-WAN Key Features:**
- Replaces expensive MPLS circuits with encrypted internet tunnels
- Centralized policy management across all branch locations
- Dynamic path selection — routes traffic over the best available link
- Enables **fully automated provisioning** of network links and appliances

---

## 📌 Slide 5 — SASE Explained

### What is SASE? *(say it: "sassy")*
**Secure Access Service Edge** — the convergence of **SD-WAN + cloud-delivered security** into a single service.

**SASE bundles these security functions:**

| Component | What It Does |
|---|---|
| **CASB** | Cloud Access Security Broker — monitors/controls cloud app usage |
| **FWaaS** | Firewall as a Service — cloud-native firewall |
| **ZTNA** | Zero Trust Network Access — "never trust, always verify" |
| **SWG** | Secure Web Gateway — filters malicious web traffic |
| **SD-WAN** | Encrypted WAN connectivity layer |

> 🔑 **Why it matters:** SASE moves security inspection to the **cloud edge** — right where users and data actually are.

---

## 📌 Slide 6 — Real-World Scenario: Remote Work & VPN vs. SASE

### 🏠 The Problem: Traditional VPN Backhauling

> *Imagine Sarah, a remote worker in Chicago. She opens Salesforce (a SaaS app). With a traditional VPN:*

```
Sarah's Laptop → VPN Tunnel → Corporate Data Center (NYC) → Internet → Salesforce
```

**Result:** High latency, degraded performance, bottlenecked bandwidth — all traffic hairpins through HQ.

### ✅ The Solution: SASE Direct-to-Cloud

```
Sarah's Laptop → SASE PoP (nearest cloud edge) → Salesforce
```

**Result:** Traffic inspected and secured at the nearest **Point of Presence (PoP)** — faster, safer, no backhauling.

> 💬 *"Why are we routing Chicago traffic through New York just to reach a cloud app? SASE fixes that."*

---

## 📌 Slide 7 — Comparison Table: MPLS/VPN vs. SD-WAN vs. SASE

| Feature | Traditional MPLS/VPN | SD-WAN | SASE |
|---|---|---|---|
| **Transport** | Dedicated leased lines | Commodity internet (encrypted overlay) | Cloud-delivered |
| **Security** | Perimeter firewall | Centralized policy enforcement | Integrated CASB, FWaaS, ZTNA, SWG |
| **Remote User Support** | VPN backhaul to HQ | Improved routing, still HQ-centric | Direct-to-cloud via nearest PoP |
| **Performance** | Predictable but expensive | Better than MPLS, cost-effective | Optimized — no backhauling |
| **Management** | Manual, hardware-based | Centralized, software-driven | Fully cloud-managed |
| **Zero Trust Support** | ❌ Implicit trust once inside | ⚠️ Partial | ✅ Built-in ZTNA |
| **Cost** | High (dedicated circuits) | Medium | Subscription-based |

---

## 📌 Slide 8 — Diagram Walkthrough: SASE Architecture

```
[ Remote User / Home Office ]
          |
          ▼
[ SASE Point of Presence (PoP) — Cloud Edge ]
   ┌──────────────────────────────────┐
   │  ZTNA  │  SWG  │  CASB  │ FWaaS │
   └──────────────────────────────────┘
          |                    |
          ▼                    ▼
  [ SaaS Apps ]        [ Corporate Cloud Resources ]
  (Salesforce,          (AWS, Azure, Private Apps)
   Microsoft 365)
```

**Walk the class through this flow:**
1. Remote user connects → hits the **nearest SASE PoP** (not HQ)
2. ZTNA verifies identity — *"never trust, always verify"*
3. SWG filters web traffic for malware/phishing
4. CASB monitors cloud app access and enforces DLP
5. FWaaS applies firewall rules at the cloud edge
6. User gets **direct, secure access** to cloud resources — no backhaul

---


## 📌 Slide 10 — One-Page Summary Sheet

> *(Submit this to the class question bank)*

| Term                      | Definition                                                                      |
| ------------------------- | ------------------------------------------------------------------------------- |
| **SD-WAN**                | Overlay WAN using encrypted internet links with centralized policy control      |
| **SASE**                  | Convergence of SD-WAN + cloud security (CASB, FWaaS, ZTNA, SWG)                 |
| **CASB**                  | Monitors and controls cloud application usage                                   |
| **FWaaS**                 | Cloud-native firewall delivered as a service                                    |
| **ZTNA**                  | Zero Trust Network Access — "never trust, always verify"                        |
| **SWG**                   | Filters malicious web traffic at the cloud edge                                 |
| **PoP**                   | Point of Presence — SASE inspection node closest to the user                    |
| **Backhauling**           | Routing remote traffic through HQ before reaching the internet — causes latency |
| **DLP**                   | Data Loss Prevention — prevents unauthorized data exfiltration                  |
| **Automated Patching**    | Cloud-native tools that auto-deploy OS/instance updates                         |
| **User Provisioning**     | Providing User accounts, access                                                 |
| **Resource Provisioning** | Adjusting infrastructure resources for company needs                            |

**Key Exam Reminders:**
- SASE = SD-WAN + security stack, cloud-delivered
- SASE solves the **backhauling problem** for remote workers
- ZTNA is a *component* of SASE — not the same thing
- Physical perimeter firewalls **fail** when users access SaaS directly from home

---
# MISC

**Policy Management (within Zero Trust)**

*Policy Engine*
	 responsible for making access control decisions based on pre-defined policies and contextual information about the subject/system.

*Policy Enforcement Point*
	responsible for enforcing the access control decisions made by the policy engine

*Subject/System*
	refers to the entity (user or device) that is requesting access to a resource, which needs to be authenticated before being granted access

*Policy Administrator*
	Outlines and creates policy and inherent systems