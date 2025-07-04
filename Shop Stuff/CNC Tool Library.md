# Establishing a Master Tool Library Across Mazak Parts

## Purpose

Provide a clear, data‑backed case for transitioning from part‑specific tool sheets to a shared “master tool” framework, where identical tool assemblies are reused across multiple aerospace parts. Although our shop routinely machines **≈300 active part numbers**, this initial trial focuses on **40 representative parts** to validate the concept at a manageable scale. The goal is to quantify the time savings and reduction in human error for both Engineering and the Tool Room.

--- where identical tool assemblies are reused across multiple aerospace parts. The goal is to quantify the time savings and reduction in human error for both Engineering and the Tool Room.

---

## 1  Current Workflow ("One‑Part, One‑List")

- Production engineers manually create each tool sheet, typing Mazak tool names and details by hand for every part—this data entry is prone to typos or mismatches, whereas the new Excel system pulls names directly from Mazak programs and ensures perfect alignment.
    
- Tool setters build every tool from scratch—even when an identical assembly was just used on a previous job.
    
- Knowledge of prior builds lives in tribal memory; there is no systematic link between parts that share tools.
    

### Pain Points

|Area|Impact|
|---|---|
|Setup time|Re‑building common tools for every part inflates setup minutes/hours—**≈ 7 min per tool** on average.|
|Consistency|Same tool name is rebuilt differently across parts (e.g., two parts list `Endmill .5A` but each specifies a different holder, cutter, or stick‑out), leading to duplicate assemblies and setup mistakes.|
|Scrap & Rework|Re‑built tools may deviate in stick‑out or holder, leading to mismatches with proven programs.|
|Presetter integration|Lack of unique tool identifiers blocks our Zoller database from recognizing the intended tool, disabling automated checks like min/max stick‑out and run‑out limits.|
|Inventory|Extra inserts & holders are consumed to duplicate tools already available.|

---

## 2  Proposed Solution: Master Tool Relationship

1. **Unique Tool Key**   Mazak programs already encode three fields → **Tool Name + Nominal Ø + Letter** (e.g., `Endmill .5A`).
    
2. **Relational Mapping**   Create a database table that maps each unique tool key to **one** fully‑defined assembly (holder, stick‑out, inserts, etc.).
    
3. **Part–Tool Join Table**   Parts link to tools instead of defining them; if two parts call `Endmill .5A`, they reference the same record.
    
4. **Permanent Setup**   Maintain ~175 "core" assemblies permanently loaded in the tool crib/turrets; only truly new tools require a build.
    

---

## 3  Pilot Results (40 of ~300 Active Parts Consolidated) Parts Consolidated)

|   |   |   |   |
|---|---|---|---|
|Metric|Before (per‑part lists)|After (master list)|Δ Improvement|
|Unique tool assemblies|≈800 builds (≈20 tools × 40 parts)|**175** total|**‑78 %**|
|Avg. first‑time setups/week|**≈15**|**≈1** (expected once master library is fully adopted)|**‑93 %**|
|Setup minutes saved/run|—|**≈80‑120 min** (20 tools × 4‑6 min saved)|—|
|Reported build errors (per week)|**≈10**|**0** so far|**‑100 %**|

> **Finding:** For the 40‑part pilot (≈13 % of our 300‑part catalog), a core library of **175 tools** satisfied all needs, eliminating **≈625 duplicate builds** and demonstrating the scalability of this approach.

---

## 4  Benefits

- **Usage & Cost Tracking** – Because the core tools stay built (currently used only on aluminum parts), we can log spindle‑on minutes per tool, revealing true cost‑per‑cut and improving forecasts for insert and holder spend.
    
- **Time Savings** – Tool setters pull a proven assembly instead of building from scratch; with a baseline of **~7 min build time per tool**, preliminary logs show a **4‑6 min reduction per tool**, translating to **80‑120 min saved** on a typical 20‑tool setup. The reclaimed time allows setters to **inspect stored tools for wear or damage**, preventing unexpected failures.
    
- **Error Reduction** – Reusing the exact holder & stick‑out eliminates trial cuts and dimensional variance.
    
- **Predictable Cycle Times** – Programs reference identical g‑code offsets and proven wear data.
    
- **Lower Inventory Spend** – Fewer redundant holders and inserts purchased.
    
- **Scalability** – Each new part added rarely needs new tools; simply joins existing ones.
    

---

## 5  Next Steps & Action Items

|   |   |   |
|---|---|---|
|Owner|Task|Due|
|Production Eng.|Validate master‑tool keys for remaining 120 parts|[date]|
|Tool Room Lead|Identify physical storage for ~200 permanent assemblies|[date]|
|IT / DBA|Enhance and maintain the existing Excel‑based Part–Tool join table (auto‑imports from Mazak programs & Solutionware Tool Manager; add refresh automation and version backups)|[date]|
|Production Eng.|Update legacy tool sheets to the new Excel‑based tool sheets|[date]|

---

## 6  Open Questions / Data Needed

- Validate the assumed **7 min average build time per tool** with a brief time study to tighten ROI.
    
- Historical scrap/rework hours attributable to incorrect tool builds.
    
- Capacity in existing turrets/crib for permanent setups.
    

---

## 7  Conclusion

Moving to a relational master‑tool system leverages Mazak’s existing naming structure to slash duplicate work and de‑risk setups. The 40‑part pilot demonstrates a compelling **78 % reduction** in unique builds. Scaling facility‑wide positions the shop for faster change‑overs, consistent quality, and lower tooling costs.

> **Recommendation:** Prioritize onboarding the **top 100 most‑run setups per year** into the master tool library first, then expand incrementally and adjust SOPs accordingly.