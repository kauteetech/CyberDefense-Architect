# CyberDefense Architect — Citation Map

**App version 1.9.0 · Verification date 15 August 2026 · MITRE ATT&CK Enterprise v19.2**

This document exists so that anyone who challenges a claim in the simulator can
check it in under a minute, and so that anyone who wants to quote the simulator
knows which parts are quotable and which are not.

It is in two halves. The first lists claims that have an external source. The
second lists claims that have none. **The second half is the more important one.**

---

## How to read this

The simulator contains four kinds of content:

| Kind | Example | Sourced? |
|---|---|---|
| Technique identifiers | `T1566.002` | Yes — MITRE |
| Mitigation identifiers | `M1032` | Yes — MITRE |
| Vendor and product names | "VMware vDefend" | Yes — vendor's own material |
| Efficacy weights, thresholds, narratives, impact figures | `edr 0.65` | **No — author judgement** |

If a number in this app has a decimal point, assume it is my judgement unless
this document says otherwise.

---

# Part 1 — Sourced claims

## 1.1 Attack techniques (T-numbers)

All 46 technique identifiers and their names were checked against the live
MITRE index, not recalled from memory. Four errors were found and corrected
during verification; they are listed below because a corrected error is worth
more to a reader than a clean list.

**Primary source — full Enterprise technique and sub-technique index**
<https://attack.mitre.org/techniques/enterprise/>

| Technique | Where used | Source |
|---|---|---|
| T1030 Data Transfer Size Limits | DNS tunnelling — throttling below alert thresholds | <https://attack.mitre.org/techniques/T1030> |
| T1606.001 Forge Web Credentials: Web Cookies | API scraping — token role-claim tampering | <https://attack.mitre.org/techniques/T1606/001/> |
| T1589.003 Gather Victim Identity Information: Employee Names | Credential harvest — reconnaissance | <https://attack.mitre.org/techniques/T1589/003/> |
| T1205 Traffic Signaling | **Checked and rejected.** It is port knocking and magic packets, not rate throttling. | <https://attack.mitre.org/techniques/T1205/> |

### Corrections made during verification

| Was | Now | Why it was wrong |
|---|---|---|
| `T1205` Traffic Signaling | `T1030` Data Transfer Size Limits | T1205 is port knocking. It has nothing to do with staying under volumetric thresholds. |
| `T1656` Impersonation | `T1606.001` Forge Web Credentials: Web Cookies | T1656 is social-engineering impersonation (BEC). It has also been restructured as `T1684.001` in v19, so the identifier was heading out of date regardless. |
| `T1589.002` Email Addresses | `T1589.003` Employee Names | The step describes harvesting names and job titles, which is `.003`. |
| "Remote Services: SMB / RDP" | "Remote Services: RDP and SMB" | Label order contradicted the IDs. `T1021.001` is RDP; `T1021.002` is SMB / Windows Admin Shares. |
| "Exfiltration Over Alternative Protocol: DNS" | "Exfiltration Over Alternative Protocol" | The colon implied a DNS sub-technique. None exists under `T1048` by that name. |

## 1.2 Mitigations (M-numbers)

All 44 enterprise mitigations were retrieved as a complete list and every
control's mapping checked against it. **All 26 mitigation references were
already correct.** One was tightened for precision: the network IPS control
now maps to `M1031 Network Intrusion Prevention` rather than the broader
`M1050 Exploit Protection`.

**Source** — <https://attack.mitre.org/mitigations/enterprise/>

## 1.3 Vendor and product names

102 vendor strings appear in the knowledge base. They are named for
orientation only — no endorsement, no ranking, no commercial relationship.
Names most likely to have changed were checked against the vendor's own
material rather than a reseller or comparison page.

| Claim | Source |
|---|---|
| VMware vDefend Distributed Firewall is the current name for the former NSX security line | <https://www.vmware.com/products/security/vdefend-distributed-firewall> |
| vDefend Distributed Firewall — product documentation | <https://techdocs.broadcom.com/us/en/vmware-security-load-balancing/vdefend/vdefend-firewall/4-2/vdefend-distributed-firewall.html> |
| Abnormal Security legally renamed **Abnormal AI, Inc.** in April 2025 | <https://abnormal.ai/newsroom/press-releases/announcing-abnormal-ai> |
| BloxOne branding retired; the product is **Infoblox Threat Defense** | <https://www.infoblox.com/products/threat-defense/> |
| Carbon Black divestment was abandoned; it remains in Broadcom's portfolio | <https://www.csoonline.com/article/1310164/broadcom-pauses-sale-of-carbon-black-as-euc-deal-goes-through.html> |

### Later additions (v1.6.0–1.7.0)

A 27th control, **Distributed IDS/IPS (east-west)**, was added after review
feedback that the model had no way to represent inspection of internal
traffic. The perimeter IPS control was renamed to make its north-south scope
explicit. Vendor names for the new control were taken from vendor material
already cited above.

A 28th control, **Deception & decoys**, was added in v1.8.0. It carries no
ATT&CK mitigation ID because none maps cleanly; deception is covered by MITRE
Engage, the denial and adversary-engagement framework that replaced MITRE
Shield — <https://engage.mitre.org/>. The micro-segmentation and distributed
IDS/IPS entries were also expanded to state their own structural limits
(intra-group blindness, encrypted east-west traffic, data-plane coverage).

### Vendor corrections made

| Was | Now |
|---|---|
| Abnormal Security | Abnormal AI |
| Infoblox BloxOne Threat Defense | Infoblox Threat Defense |
| Aruba ClearPass | HPE Aruba Networking ClearPass |

### Vendor names *not* individually verified

The remaining names were assessed as low-risk (stable brands, or recent
enough that a change was unlikely) and were **not** each checked against
source. If precision matters for a specific one, check it before quoting.
Vendor naming decays faster than anything else in this app — assume the list
is stale after roughly six months.

## 1.4 Regulatory references

One appears in the app, in the API scraping scenario.

| Claim | Source |
|---|---|
| India's DPDP Rules were notified November 2025; substantive obligations commence 14 May 2027 | <https://www.amsshardul.com/insight/enforcement-of-the-dpdp-act-and-notification-of-the-dpdp-rules/> |

The app text was amended during verification to state the 2027 commencement
date, because the original wording implied the obligations were already in
force.

## 1.5 Attribution

Technique and mitigation identifiers are reproduced from MITRE ATT&CK®.
ATT&CK is a registered trademark of The MITRE Corporation. The efficacy
weights attached to those identifiers are mine and are not MITRE content.

---

# Part 2 — Claims with no source

Nothing in this section has a citation, because none exists. These are
positions to argue with, not findings to quote. If someone cites the
simulator's numbers in a business case, this is the section they skipped.

### The efficacy weights
Every `0.00`–`1.00` number attached to a control, for every step. Informed
judgements chosen to teach how controls relate to one another. Not measured
in any estate, not benchmarked, and no vendor's product was tested to produce
them. They are printed on screen precisely so a trainee can disagree.

### The thresholds
The 0.75 block threshold, the 0.50 detection threshold, and the rule that
three independent detections stop the chain. Modelling choices. The reasoning
is in the app's model panel; the reasoning is not evidence.

### The dwell-hour model
Hours attributed to each tactic, and the per-scenario pacing multipliers that
make the DNS and API scenarios slow. These produce the time-to-detect figure.
Chosen for plausibility.

### The impact figure
The dollar number in the exported report scales with how far the chain got and
drops when detection happens early. It is not actuarial, not drawn from breach
cost research, and not calibrated to any industry or region.

### The scenario narratives
Actors, targets, data volumes, record counts and timelines are composites
written to be plausible. They are not case studies of real incidents and
should not be attributed to any real intrusion.

### The posture presets
Which controls each preset enables, including the deliberate omission of
identity controls from the virtualisation-led preset — a teaching choice that
makes that preset perform worse on credential attacks.

### The "where this breaks in practice" notes
One per control. Field opinion, offered as opinion. Some are widely held
(untested backups are not backups); some are arguable (that most WAF failures
are deployment mode rather than detection capability). None are researched
claims.

---

# Part 3 — Re-verifying this yourself

1. **Technique and mitigation IDs.** Open the two MITRE index links, search
   the ID, confirm the name matches. Stable and quick. ATT&CK releases
   roughly twice a year; check the version banner.
2. **Vendor names.** Go to the vendor's own product page, not a comparison
   site or reseller. This is where drift happens fastest.
3. **The weights.** Cannot be verified. They can only be argued about, which
   is the intended use.

If you find an error, it is an error — please say so rather than working
around it.
