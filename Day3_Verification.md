# Day 3 — Lab 3A: Verification Matrix

**Name:** Bhavya Teja Penke
**Date:** 11 June 2025

---

## Step 1 — Prompt Used (Gemini)

> "List 5 specific statistics about Indian campus placement in 2025-2026. For each: state the number, the year, and the source organisation. Format as a numbered list."

---

## Step 2 — Gemini Output (AI-Generated Claims)

1. **₹32 LPA**
   - Year: 2025–2026
   - Source Organisation: International Institute of Information Technology (IIIT), Hyderabad (via National Institutional Ranking Framework — NIRF data)
   - Detail: Average campus placement package secured specifically by CSE graduates at the institute.

2. **94%**
   - Year: 2025–2026
   - Source Organisation: Anna University (College of Engineering, Guindy)
   - Detail: Percentage of eligible Mechanical Engineering graduates successfully placed, outpacing the IT/CSE branch rate (87%) at the same college.

3. **₹24.7 LPA**
   - Year: 2025–2026
   - Source Organisation: Birla Institute of Technology and Science (BITS), Pilani (via NIRF data)
   - Detail: Overall median campus placement package across all engineering disciplines at the institute.

4. **81%**
   - Year: 2025–2026
   - Source Organisation: RMK Group of Engineering Colleges
   - Detail: Overall student placement rate achieved by the Career Development Centre via skill-based training in VLSI, AI, and cybersecurity.

5. **₹12,02,209**
   - Year: 2025–2026
   - Source Organisation: Thapar Institute of Engineering and Technology (TIET)
   - Detail: Exact weighted average package secured during campus recruitment, as recorded in the active university placement data tracker.

---

## Step 3 — Perplexity Verification

**Prompt used for each claim:**

> "Verify: 'Here are 5 specific statistics regarding Indian campus placements for the 2025–2026 academic cohort: [full claim text]'. Cite 2 primary sources."

**Perplexity output summary:**

The block of 5 statistics is **not verified as accurate or sourced as described**. At least some numbers are inconsistent with what is publicly available from primary placement reports. The claims mix broadly plausible magnitudes with specific, oddly precise numbers that are not traceable to official reports, contain misattributions (e.g. "via NIRF" for branch-specific averages), and lack two primary sources that independently confirm all five statistics with the exact wording and numbers provided.

---

## Step 4 — Verification Matrix

| # | Claim | AI Source (Gemini) | Perplexity Check URLs | Primary Source URL | Verdict |
|---|-------|--------------------|-----------------------|--------------------|---------|
| 1 | ₹32 LPA average CSE package, IIIT Hyderabad, 2025–26, via NIRF | IIIT Hyderabad via NIRF | https://eduwallah.in/university/iiit-hyderabad · https://www.shiksha.com/articles/iiit-hyderabad-recruiting-companies-placements-data-blogId-121605 | https://eduwallah.in/university/iiit-hyderabad-indian-institute-technology-hyderabad-20/placement | PARTIAL |
| 2 | 94% Mechanical placement rate (vs 87% CSE), Anna University CEG, 2025–26 | Anna University / CEG | https://www.linkedin.com/posts/rkbatham_indiaplacements-campushiring-iit-activity-7377445593625014273-gDqu | No official CEG T&P report found | NO PRIMARY SOURCE FOUND |
| 3 | ₹24.7 LPA median package (all branches), BITS Pilani, 2025–26, via NIRF | BITS Pilani via NIRF | https://www.collegesimplified.in/post/average-placement-package-by-college-2026-the-comprehensive-salary-report | https://www.collegesimplified.in/post/average-placement-package-by-college-2026-the-comprehensive-salary-report | FALSE |
| 4 | 81% overall placement rate, RMK Group of Colleges, 2025–26 | RMK Group CDC | No primary placement report or T&P page found | No primary source found | NO PRIMARY SOURCE FOUND |
| 5 | ₹12,02,209 weighted average package, Thapar Institute (TIET), 2025–26 | TIET placement tracker | https://colleges.freejobalert.com/colleges/thapar-institute-of-engineering-and-technology · https://colleges.freejobalert.com/colleges/thapar-institute-of-engineering-and-technology/placements | https://colleges.freejobalert.com/colleges/thapar-institute-of-engineering-and-technology/placements | PARTIAL |

---

## Tally

| Verdict | Count |
|---------|-------|
| VERIFIED | 0 |
| PARTIAL | 2 |
| FALSE | 1 |
| NO PRIMARY SOURCE FOUND | 2 |

> ✅ **Acceptance check passed** — 4 out of 5 claims are non-VERIFIED (2 PARTIAL, 1 FALSE, 2 NO PRIMARY SOURCE FOUND).

---

## Step 5 — Reflection Paragraph

The claim that looked most authoritative but was actually weakest was claim **#3**: *"₹24.7 LPA overall median package across all engineering disciplines, BITS Pilani, 2025–26, via NIRF."* Gemini cited NIRF data confidently, and the specific decimal figure (₹24.7 LPA) gave it the appearance of precision and credibility — it felt like a number someone had carefully calculated. Perplexity initially appeared to support a BITS Pilani median figure, but when I opened the primary source, BITS Pilani's placement data and aggregator reports consistently show B.Tech average packages in the ₹28–29 LPA range for recent years, making ₹24.7 LPA not just unverifiable but directionally inconsistent with all available data. Furthermore, NIRF does not publish branch-wise or cycle-specific median figures in this format — the attribution itself was fabricated. The lesson: a precise-looking decimal is not evidence of accuracy; it can just as easily be a hallucinated artefact of a confident model. Confidence does not equal correctness. The verification step belongs to the human — every time.

---

## Acceptance Checklist

- ✅ Matrix has all 5 rows × 5 columns filled (claim, AI source, Perplexity check, primary source URL, verdict)
- ✅ At least 1 verdict is PARTIAL, FALSE, or NO PRIMARY SOURCE FOUND (4 out of 5)
- ✅ Reflection paragraph identifies the weakest-sounding-yet-strongest-looking claim (#3 — BITS Pilani median)
- ✅ Submitted as `Day3_Verification.md` to ai-mentor-portfolio repo

---

## Reference Sources

- [NIRF](https://nirf.org)
- [NASSCOM](https://nasscom.in)
- [AICTE](https://www.aicte-india.org)
- [India Skills Report — Wheebox](https://wheebox.com/india-skills-report.htm)
- [Aspiring Minds](https://www.aspiringminds.com)
- [Eduwallah — IIIT Hyderabad placements](https://eduwallah.in/university/iiit-hyderabad-indian-institute-technology-hyderabad-20/placement)
- [Shiksha — IIIT Hyderabad placement data](https://www.shiksha.com/articles/iiit-hyderabad-recruiting-companies-placements-data-blogId-121605)
- [CollegeSimplified — average packages 2026](https://www.collegesimplified.in/post/average-placement-package-by-college-2026-the-comprehensive-salary-report)
- [FreeJobAlert — Thapar placements](https://colleges.freejobalert.com/colleges/thapar-institute-of-engineering-and-technology/placements)

---
