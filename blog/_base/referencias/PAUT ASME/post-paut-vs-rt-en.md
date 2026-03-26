# Phased Array (PAUT) as a Replacement for Radiography per ASME: Complete Guide

**Requirements, costs, procedure qualification, and the Level III dilemma**

**Tags:** Phased Array PAUT, radiographic testing RT, ASME BPVC, ASME Code stamp, NDE procedure, ASNT Level III, NDT personnel certification

**By Dan Yamashita · Level III ASNT/PCN · SimpleNDT**

---

## What Is Phased Array Ultrasonic Testing (PAUT)

Phased Array Ultrasonic Testing (PAUT) is an advanced nondestructive testing (NDT) technique that uses multi-element transducers to electronically generate and steer ultrasonic beams. Unlike conventional UT — which relies on a single crystal emitting a fixed beam — PAUT individually controls dozens of piezoelectric elements through programmable time delays, enabling electronic focusing, beam deflection, and multi-angle sweeping simultaneously.

The practical outcome: a single PAUT scan produces sectorial (S-scan) or linear (E-scan) images in real time, covering the full weld volume with superior resolution and traceability compared to manual ultrasonics. When combined with encoders and mechanized scanners, PAUT generates complete digital records — raw data files — that can be reanalyzed at any time, providing an auditability that radiography only achieves through the physical film itself.

The technique is governed by the ASME Boiler and Pressure Vessel Code (ASME BPVC), Section V, Article 4, which establishes specific requirements for ultrasonic examination of welds, including mandatory appendices dedicated to Phased Array. The formal permission to substitute radiography with PAUT in pressure vessels was introduced through the landmark Code Case 2235 and is now directly incorporated into ASME BPVC Section VIII, Division 2, Paragraph 7.5.5.

---

## RT vs. PAUT: Advantages and Disadvantages

Choosing between radiographic testing (RT) and Phased Array (PAUT) is not a matter of one method being universally superior. Each technique has domains where it inherently excels.

### Where Radiography (RT) Excels

Radiography is more reliable at detecting **volumetric discontinuities** such as clustered porosity and slag inclusions. The density contrast these defects produce in the image is unmistakable. Additionally, radiographic film (or digital DR/CR images) provides a permanent visual record that is intuitive and readily interpretable — including for auditors who are not versed in acoustics. RT is also less sensitive to surface roughness and part geometry: if the radiation beam penetrates, the image appears.

Another point rarely discussed: the interpreter's learning curve for RT is shorter. A competent Level II in radiography can evaluate films within months. Interpreting volumetric PAUT data (overlaid C-scan, S-scan, B-scan views) requires significantly greater technical maturity.

### Where Phased Array (PAUT) Excels

PAUT is dramatically superior at detecting **planar defects** — cracks, lack of fusion, and lack of penetration. These are precisely the discontinuities that fracture mechanics classifies as critical to structural integrity. A crack with an opening of tenths of a millimeter can be completely invisible to radiography if the X-ray beam is not perfectly parallel to the flaw plane. For PAUT, that same crack acts as an acoustic mirror, reflecting sound massively back to the transducer.

Additionally, PAUT offers:

- **Real-time results**, with no chemical processing or waiting period.
- **Sizing capability** — direct measurement of defect height and length, essential for fitness-for-service evaluation per ASME VIII Div. 2.
- **No ionizing radiation**, eliminating the entire chain of radiation protection controls: regulatory licensing, dosimetry, area evacuation, shielded enclosures.
- **Inspection parallel to production** — no factory shutdown required for area isolation, as with radiography.

### Comparative Summary

| Criterion | Radiography (RT) | Phased Array (PAUT) |
|---|---|---|
| Volumetric defects (porosity, slag) | Superior | Adequate |
| Planar defects (cracks, LOF) | Limited | Superior |
| Permanent, auditable record | Film / digital image | Digital raw data |
| Ionizing radiation | Yes (Ir-192, Se-75, X-ray) | No |
| Real-time results | No | Yes |
| Defect sizing | Not direct | Yes |
| Production impact (area isolation) | High | None |
| Sensitivity to roughness/geometry | Low | Medium to high |

---

## Costs: Capital Investment vs. Operating Expense

The cost equation between RT and PAUT inverts depending on what you measure — and this is where many managers miscalculate.

### Equipment Cost (CAPEX)

PAUT requires a significantly higher initial investment. Phased Array instruments capable of ASME-compliant RT substitution (such as Olympus OmniScan, Eddyfi Gekko/Mantis, or equivalents) typically cost US$50,000 to US$150,000 depending on configuration. Add transducers, wedges, mechanized scanners, and analysis software, and a complete field setup can easily exceed US$200,000.

By comparison, an Iridium-192 source with collimator and safety accessories, or a portable X-ray generator, requires a lower initial outlay — typically US$30,000 to US$80,000.

### Operating Cost (OPEX)

This is where the equation flips. The cost per meter of weld inspected with PAUT is drastically lower than radiography:

- **RT:** Film or phosphor plates, processing chemicals (for conventional film), periodic source replacement (Ir-192 half-life: ~74 days), dosimeters, environmental monitoring, larger crews (operator + radiation safety officer), regulatory licensing. Add the indirect cost of production downtime for area isolation.
- **PAUT:** Couplant (gel or water) and mechanical wear on wedges. No significant consumables. A PAUT crew is typically smaller and can operate continuously without impacting other activities.

### Productivity Impact

Field estimates indicate a PAUT crew can inspect approximately **60 welds per 10-hour shift**, while an RT crew typically achieves around **30 welds in the same period** — half the throughput. The difference comes from radiography's dead time: source/film setup, area isolation, exposure duration, processing, and film evaluation.

For manufacturers with serial production and high weld volume, PAUT pays for itself quickly. For those inspecting a few pieces per year, radiography may be more economically rational — especially considering the cost of procedure qualification, as discussed below.

---

## Procedure Qualification: RT vs. PAUT — A Drastic Difference

This is the point that separates theory from practice, and where many fabricators are caught off guard.

### Radiography: Continuous, Simplified Qualification

Radiographic procedure "qualification" is, in practice, continuous and self-verifying. ASME BPVC Section V, Article 2 requires each radiographic exposure to include an Image Quality Indicator (IQI, also called a penetrameter). If the film or digital image reveals the required hole or wire with the correct optical density, the procedure has demonstrated its sensitivity on that exposure. No test blocks with artificial cracks are required. No formal Performance Demonstration exists.

This means RT procedure qualification is **standard and straightforward**. For a shop undergoing ASME Code stamp certification or recertification (U, U2, S, R, PP stamps), the demonstration to the Authorized Inspector (AI) during the audit is relatively simple: the written procedure, IQIs, exposure technique, and films speak for themselves.

### Phased Array: Formal Performance Demonstration (PDQ)

To replace radiography, ASME BPVC Section V, Article 4, Mandatory Appendix IX requires a formal **Performance Demonstration (PDQ)**. In practice, this means:

1. **Fabricating demonstration blocks (mockups)** — replicas of the production joint (same material, thickness, groove configuration, and welding process).
2. **Inserting artificial flaws** — at least 3 defects (surface and subsurface) with controlled dimensions.
3. **Running the scan and proving detection** — the operator must detect and size the flaws within millimetric tolerances (typically ±0.5 mm for height).

Furthermore, PAUT has an **extensive list of Essential Variables** (Table T-421 of ASME V Art. 4). Any change in:

- Joint configuration and thickness
- Propagation angles and technique (S-scan, E-scan)
- Focal laws (depth, plane, number of elements)
- Transducer/wedge type, frequency, and size
- Sizing method

...requires the **entire demonstration process to be repeated.** This includes fabricating new mockups if the material or thickness changes.

### Practical Implication: When Each Method Makes More Sense

The conclusion is direct:

**Radiography is more suitable for:**
- ASME Code stamp certification and recertification processes, where demonstration to the AI must be quick and standardized.
- Inspection of **few pieces**, non-serial parts, or highly varied joint configurations — since each different PAUT configuration would require a specific qualification.
- Fabricators with low volume or high product diversity.

**Phased Array is more suitable for:**
- Serial production with **high weld volume in repetitive joint configurations** — where the procedure qualification investment is amortized.
- Projects under ASME Section VIII, Division 2, where fracture mechanics assessment requires precise defect sizing.
- Environments where ionizing radiation is restrictive (offshore platforms, operating plants, refineries).

For fabricators needing [PAUT procedures compliant with ASME V](https://simplendt.com.br/servicos/phased-array), SimpleNDT develops complete documentation including scan plans, beam plotting, and personnel qualification.

---

## Level III for Phased Array under ASME: The Chicken-and-Egg Dilemma

This is one of the most critical — and least discussed — issues in ASME-compliant PAUT implementation.

### Level III Responsibilities in PAUT

Per the ASME BPVC, the Level III responsible for the PAUT program holds the following duties:

- Development and approval of the **examination procedure** and the **Scan Plan** (acoustic and geometric modeling of beam coverage over the joint).
- **Specification of calibration and demonstration blocks** per Code requirements (material, thickness, type and dimensions of artificial flaws).
- Conducting or supervising the **Performance Demonstration (PDQ)**.
- **Qualification and certification of Level I and Level II personnel** in Phased Array, per the company's Written Practice.

### The ASME Requirement for Level III

ASME BPVC Section V and the SNT-TC-1A Recommended Practice require that the Level III responsible for the PAUT [personnel qualification](https://simplendt.com.br/servicos/qualificacoes) program meet specific competency requirements in the method. In general terms, this means being certified or having demonstrated practical competence in UT Phased Array — being Level III in conventional UT alone is not sufficient.

Under the SNT-TC-1A scheme (employer-based certification), the company's Level III is the one who trains, evaluates, and certifies Level I and II personnel. But here lies the dilemma: **for a Level III professional to sit for the Level II practical exam in PAUT — necessary to demonstrate method competence — they must be evaluated by another Level III who already meets the ASME requirements for Phased Array.**

And where is that other Level III? If very few professionals in a given country fully meet ASME requirements for PAUT, the first Level III attempting to qualify encounters a circular barrier: they need someone qualified to qualify them, but that someone faces the same problem. This is, in essence, a **chicken-and-egg dilemma**.

### The Solution: Go to the Source

The way out of this impasse is to seek qualification directly at examination centers that have the infrastructure and already-qualified professionals — which, in practice, means **traveling to the United States** to sit for exams under conditions that fully comply with ASME and ASNT requirements.

This is the path [SimpleNDT](https://simplendt.com.br/sobre) took. Dan Yamashita completed his Phased Array examinations in the US, obtaining dual Level III certification — ASNT (SNT-TC-1A) and PCN (ISO 9712) — in both conventional UT and Phased Array, in full compliance with ASME Code requirements.

The key point here is structural, not commercial: in the SNT-TC-1A employer-based certification chain, **the entire legitimacy of a company's PAUT program rests on the qualification of its Level III.** If the Level III does not meet the requirements, the entire chain below — Level II and Level I — is compromised. This is precisely what ASME auditors verify during [Code stamp audits](https://simplendt.com.br/servicos/auditorias-asme).

---

## FAQ — Frequently Asked Questions

### Does ASME allow replacing radiography with Phased Array in every situation?

No. The substitution is permitted under specific conditions established by ASME BPVC Section V, Article 4, Mandatory Appendix IX, and referenced by Section VIII (Div. 1 and Div. 2). Code Case 2235 was the original milestone, now incorporated into Div. 2, Par. 7.5.5. The substitution requires advanced techniques (PAUT and/or TOFD) with encoded scanning — conventional manual UT is not accepted as a substitute. Additionally, the organization must complete a formal Performance Demonstration (PDQ) with demonstration blocks containing artificial flaws.

There are also **minimum thickness restrictions**. ASME Section VIII, Division 2 permits the substitution for joints with thickness equal to or greater than 6 mm (¼ in.). ASME Section I requires a minimum of 13 mm (½ in.), although Code Cases exist that extend applicability to the 6–13 mm range. The limits vary by applicable Code section and must be verified on a case-by-case basis.

### Which method is better for obtaining the ASME Code stamp: radiography or Phased Array?

It depends on context. For ASME Code stamp certification and recertification processes — especially if the shop has varied production and low volume — radiography is more practical because procedure qualification is simpler and universal. Phased Array is more advantageous for serial production with repetitive joint configurations, where the procedure qualification investment is justified by productivity gains and the elimination of ionizing radiation.

### Do I need a Level III specifically in Phased Array, or is Level III in conventional UT enough?

To meet ASME requirements, the Level III responsible for the PAUT program must demonstrate specific competence in the method. Being Level III in conventional UT alone is insufficient to approve scan plans, validate Performance Demonstrations, and certify Level II personnel in Phased Array. This is one of the most common nonconformities found in ASME audits involving PAUT.

### What happens if my Level III doesn't meet ASME requirements for PAUT?

The entire personnel certification chain is compromised. If the Authorized Inspector finds that the Level III lacks demonstrable PAUT qualification, reports issued by Level II personnel certified by that individual may be retroactively invalidated. This can result in major findings during the audit and, in the worst case, suspension of the ASME Code stamp.

### Why are so few Level IIIs in Brazil qualified in PAUT per ASME?

Because the process is circular: to qualify in PAUT as a Level III under the SNT-TC-1A scheme, one must be evaluated by another Level III already qualified in the method. Since PAUT is a relatively recent specialization and the Brazilian market has historically relied more heavily on radiography, very few professionals started the cycle. The practical solution is to seek qualification directly in the US, where the infrastructure and qualified professionals already exist — exactly the path SimpleNDT took.

### Is Phased Array always more expensive than radiography?

No. PAUT has higher equipment cost (CAPEX) but drastically lower operating cost (OPEX). For high weld volumes, PAUT is significantly cheaper per meter inspected. For low volume or one-off pieces, radiography may be more economical given that it does not require the investment in procedure qualification specific to each joint configuration.

### Does PAUT procedure qualification cover any thickness and material?

No. Each combination of material, thickness range, and joint configuration is an Essential Variable per Table T-421 of ASME V Art. 4. Changing any of these variables requires a new Performance Demonstration with specific mockups. This is why PAUT is more economical for serial production — the qualification is done once and applied to hundreds of identical joints.

It is also worth noting that the RT-to-PAUT substitution has **minimum thickness limits** that vary by Code section: 6 mm (¼ in.) for ASME Section VIII Div. 2, and 13 mm (½ in.) for ASME Section I (with Code Cases available for the 6–13 mm intermediate range). Joints below these thresholds are not eligible for the substitution and must continue to be inspected by radiography.

### Can I use conventional manual UT to replace radiography per ASME?

No. ASME restricts the substitution exclusively to advanced techniques with encoded scanning and continuous digital recording — PAUT and/or TOFD. Conventional manual UT lacks the traceability and reproducibility required by the Code to replace the permanent record that radiography provides.

---

## Next Step

If your company is evaluating the transition from radiography to Phased Array, or needs a qualified PAUT Level III per ASME for audits, procedures, or personnel qualification, [SimpleNDT](https://simplendt.com.br/servicos/phased-array) can help.

Dan Yamashita holds Level III certification from both ASNT and PCN in conventional UT and Phased Array, with exams completed in the United States in full compliance with ASME requirements. He works on procedure development, scan plans, Performance Demonstrations, and Code stamp audit support.

[Contact SimpleNDT via WhatsApp](https://wa.me/+5511991612503) or visit [simplendt.com.br/contato](https://simplendt.com.br/contato).

---

## Metadata — EN

- **Title tag:** Phased Array vs Radiography per ASME: Complete Guide
- **Meta description:** Technical guide on replacing radiography with Phased Array (PAUT) per ASME: advantages, costs, procedure qualification, and Level III requirements.
- **URL slug:** phased-array-replacing-radiography-asme
- **Tags:** Phased Array PAUT, radiographic testing RT, ASME BPVC, ASME Code stamp, ASNT Level III, NDE procedure, NDT personnel certification
- **Primary keywords:** Phased Array replacing radiography ASME, PAUT vs RT, PAUT procedure qualification ASME
- **Secondary keywords:** Code Case 2235, scan plan, Performance Demonstration, Level III Phased Array, ASME Code stamp audit, SNT-TC-1A, ASME Section V Article 4

## Internal Links Used

1. simplendt.com.br/servicos/phased-array
2. simplendt.com.br/servicos/qualificacoes
3. simplendt.com.br/servicos/auditorias-asme
4. simplendt.com.br/sobre
5. simplendt.com.br/contato

## Suggested Future Related Posts

1. **Scan Plans for PAUT per ASME: What the Level III Must Deliver** — beam plotting, angular coverage, documentation
2. **Performance Demonstration (PDQ) per ASME: Step-by-Step PAUT Qualification** — mockups, artificial flaws, tolerances
3. **ASME Audit and NDE: The 5 Most Common Findings in Fabrication Shops** — recurring nonconformities including PAUT
4. **ASME Section VIII Div. 1 vs. Div. 2: Impact on Nondestructive Examination** — workmanship vs. fitness-for-service, joint efficiency
5. **NDT Personnel Qualification per SNT-TC-1A: The Real Role of Level III** — responsibilities, Written Practice, common pitfalls
