# The Earth Information Jukebox
## Team Project Brief

**Prepared:** 7 November 2026  
**Team:** 5 members  
**Working title:** *Hear the Heat*  
**Challenge:** NASA Space Apps Challenge 2026 — “The Earth Information Jukebox”  
**Target:** A working web app and polished demo, built during the event

---

## 1. Project at a glance

**The Earth Information Jukebox** is an accessible, educational web experience that lets students and curious members of the public explore NASA Earth observations through sound as well as sight.

The first experience, **Hear the Heat**, guides visitors through global surface temperature anomalies. A NASA Earth Information Center (EIC) temperature visualization, a data chart, concise plain-language explanations, and browser-generated sound stay connected as the visitor moves through the historical record.

**Guiding idea:** Let people listen to changes in Earth data, inspect the measurements behind the sound, and understand how the mapping works.

---

## 2. What is settled and what is proposed

### Team choices confirmed

- Team of five.
- No app or research prototype has been built yet.
- No technology stack or infrastructure has been selected.
- Non-NASA authoritative data may be used if needed; NASA is preferred.
- Desired outcome: a working app with a polished demo.
- Internal preparation target: 13 November; the NASA Space Apps event runs 14–15 November 2026.
- Primary audience: students and other people seeking knowledge.
- Landing experience: an immersive **“Listen to the Planet”** hero section.
- Content style: brief plain-language guidance first, with more detailed science available on demand.
- Initial comparison: two time periods using the same dataset and baseline.

### Recommendations in this brief

The working title, initial temperature focus, data choice, audio mapping, technical approach, and team roles below are recommendations to make the first version achievable. The team can revise them after reading the complete challenge statement and resources.

### Published challenge summary

The publicly indexed NASA Space Apps summary asks teams to build an interface, script, or application that pairs Earth Information Center visual frames with sonifications generated in real time. We interpret “generated in real time” as synthesizing sound dynamically during playback from selected observations; it does **not** necessarily mean the source measurements update live. Confirm this interpretation against the complete challenge statement and resources when available.

**Keep separate:** NASA’s challenge asks for the EIC visual/sonification pairing. The single-temperature-story scope and the interface choices below are our proposed solution.

---

## 3. Audience and experience goals

### Primary audience

Students and curious people who want to learn about Earth systems, including visitors with visual impairments and visitors who are deaf or hard of hearing.

### The experience should help visitors

1. Understand what a temperature anomaly means.
2. Hear a measurement change while seeing the same point in the data.
3. Inspect the year, value, units, source, and reference baseline.
4. Compare two historical periods without changing the dataset or baseline.
5. Use the experience without needing sound or vision alone.

### Product principles

- **Scientific traceability:** Every value can be traced to a NASA source, time period, unit, and baseline.
- **Explainable sound:** The interface explains how the selected data controls the audio.
- **Reproducibility:** The same data and mapping produce the same sound settings.
- **Honest timing:** State that GISTEMP is updated periodically; do not call it live data.
- **Accessible alternatives:** Audio deepens the story but is never the only way to understand it.
- **No unsupported causality:** Describe observed changes without implying a cause beyond the data and cited science.

---

## 4. Proposed first release: “Hear the Heat”

### Landing page and guided story

1. **Hero — “Listen to the Planet”**  
   Use a NASA Earth image or visualization with a clear headline, a short invitation, and one prominent **Listen now** button. Do not autoplay sound.

2. **A short introduction**  
   Explain that a temperature anomaly is a difference from a stated reference average. Include the data source and baseline near the chart and player.

3. **Guided listening player**  
   Pair the EIC temperature visual, a chart/timeline, the selected year and value, and generated audio. Keep these synchronized during playback.

4. **Playback controls**  
   Play, pause, stop/replay, speed, and seek. Make controls usable by keyboard, touch, and screen reader.

5. **Optional period comparison**  
   Let visitors choose Period A and Period B and listen to each independently. Display both on the same chart scale and state the shared baseline.

6. **Expandable “How the sound works” details**  
   Explain the mapping, data source, units, baseline, update cadence, limitations, and missing-data treatment in plain language.

### Keep the MVP focused

**Include:** one NASA temperature series, one paired EIC visualization, synchronized chart and audio, year/value display, core playback controls, period comparison, attribution, and accessible alternatives.

**Defer unless the core is complete:** additional Earth phenomena, a 3D globe, accounts, export, AI-generated narration, live APIs, and complex regional selection.

---

## 5. Data and sound plan

### Candidate primary dataset

**NASA GISS Surface Temperature Analysis (GISTEMP v4)**

- Global and gridded land-ocean surface temperature anomalies.
- Monthly record beginning in 1880; NASA updates the analysis approximately monthly.
- Common GISTEMP anomaly baseline: 1951–1980. Confirm the exact file and its metadata before coding.
- Use an appropriate NASA EIC temperature visual that matches the same scientific topic. Verify whether the selected visualization uses the same data version, time aggregation, smoothing, and baseline before claiming that the frames show the exact values being sonified.

**Data source:** https://data.giss.nasa.gov/gistemp/  
**EIC temperature visualization candidate:** https://earth.gov/sealevel/vital-signs/global-temperature/  
**NASA SVS temperature visualization candidate:** https://svs.gsfc.nasa.gov/5603/

### Candidate sonification mapping — test before finalizing

- **Selected year/month:** playback position; advance at a regular interval.
- **Temperature anomaly:** pitch relative to a documented reference pitch, mapped across a fixed and visible range.
- **Comparison:** listen to each selected period using the same mapping and playback speed.

Avoid making both pitch and tempo change with the same value in the first version. That can make the data harder to interpret. The reference notes propose encoding rate of change through note-transition speed; evaluate that only if there is time to test it with users and explain it clearly.

The mapping is an artistic/interaction decision, not a property of NASA’s data. Show the current measurement alongside the sound so the relationship can be checked visually.

### Data validation checklist

- Record the exact file, access date, dataset version, variable, units, time range, and baseline.
- Confirm whether the selected visualization uses monthly, annual, rolling-average, or smoothed values.
- Ensure displayed values and sonified values refer to the same aggregation and baseline, or clearly explain any difference.
- Define consistent handling for missing or invalid values; do not let silence imply zero unless that is explicitly explained.
- Credit NASA/GISS and the EIC/SVS creators as required by the selected assets.

---

## 6. Accessibility and interaction requirements

- No automatic audio playback; visitors choose when to listen.
- Full keyboard access and visible focus indicators.
- Play/pause, stop/replay, speed, and timeline controls have accessible names and state announcements.
- Display the selected year, value, unit, and explanation as text.
- Provide a chart/table alternative to the audio; do not treat a waveform alone as equivalent information.
- Use text labels and shapes as well as colour to communicate data.
- Maintain sufficient contrast, readable type, and large touch targets.
- Respect reduced-motion preferences and keep decorative movement restrained.
- Test with at least one keyboard-only user and one person unfamiliar with the project.

---

## 7. Suggested technical approach

No stack has been chosen by the team. For a small, browser-only MVP, a reasonable starting proposal is:

- **Interface:** HTML/CSS/JavaScript, or Vite with a small frontend framework if the team already knows one.
- **Sound:** browser Web Audio API; generate tones from data during playback.
- **Data:** a small, prepared NASA data file shipped with the app; avoid adding a backend or API dependency unless needed.
- **Chart:** a simple SVG/canvas chart kept synchronized with playback.
- **Hosting:** use a platform the team already knows, or provide a reliable local demo as a fallback.

This is a recommendation, not a confirmed stack. Prefer the toolchain the frontend/backend members can implement quickly and explain confidently.

---

## 8. Suggested five-person ownership

| Member | Primary ownership | Pairs with |
|---|---|---|
| 1. Frontend / UX | Landing page, layout, responsive interface, controls | Visualization, accessibility |
| 2. Data / integration | Download/prepare GISTEMP series, metadata, app data flow | Science/story, frontend |
| 3. Audio / interaction | Web Audio synthesis, playback state, mapping controls | Frontend, accessibility |
| 4. Visualization | Chart/timeline, EIC visual pairing, synchronized selection | Data, frontend |
| 5. Science / accessibility / demo | Verify claims and attribution; review keyboard and screen-reader access; prepare demo narrative and submission content | Whole team |

These are primary responsibilities rather than silos. Every member should be able to explain the data source and how the sound relates to the measurements. A separate backend service is unlikely to be necessary for the first release.

---

## 9. Preparation and event schedule

### By 13 November — preparation

- Read the complete challenge statement and NASA-provided resources.
- Confirm Kopargaon event instructions, including when project development may begin.
- Inspect the chosen EIC visualization and GISTEMP data; record source, credits, baseline, and aggregation.
- Agree on the one-story MVP, mapping hypothesis, responsibilities, and demo flow.
- Install tools and learn any needed browser-audio basics using a generic practice example.
- Sketch the interface and prepare a task board.

Do not assume that completing the competition app by 13 November is allowed. The global hackathon is scheduled for 14–15 November, and local event rules may specify when development can start. Check with the Kopargaon organizer if unclear.

### 14–15 November — build and submit

1. Start with one end-to-end path: choose a period → see the value → hear the mapped sound → understand the mapping.
2. Add the comparison and accessibility controls.
3. Check data labels, citations, the EIC pairing, and failure behavior.
4. Record a short backup demo in case the live app or network fails.
5. Submit before the official deadline shown for the event and local time zone.

---

## 10. Demo narrative

A concise demo can follow this sequence:

1. “This is the Earth Information Jukebox. It makes Earth observations available through sight and sound.”
2. Show the EIC global temperature visual and explain the anomaly baseline.
3. Press **Listen now** and point to the selected year/value as the tone changes.
4. Pause, inspect “How the sound works,” then compare two periods.
5. Show the chart/text alternative and keyboard-accessible controls.
6. Close with the NASA data source, update cadence, and what the experience helps people learn.

---

## 11. Risks and mitigations

| Risk | Mitigation |
|---|---|
| Dataset and EIC animation do not use matching time aggregation or baseline | Confirm metadata; describe the relationship accurately and label differences |
| Audio sounds engaging but obscures the measurement | Keep the mapping simple, fixed, visible, and tied to numeric values |
| Scope grows beyond the two-day event | Complete the one-data-story path before adding features |
| Network or external asset fails during demo | Bundle a permitted visual/data excerpt or provide a local fallback; preserve attribution |
| Visitors cannot use one sensory channel | Provide equivalent chart/table/text information and accessible controls |
| Asset reuse terms are unclear | Check each asset’s credits and usage terms; do not imply NASA endorsement |
| “Real-time” is misunderstood as live data | Explain that synthesis occurs during playback while GISTEMP updates periodically |

---

## 12. Reference shortlist

These links are research references, not blanket permission to reuse assets. Check individual credits, terms, and third-party material before incorporating an asset.

### Hero and Earth imagery
- NASA Blue Marble: https://visibleearth.nasa.gov/collection/1484/blue-marble
- NASA Eyes on the Earth: https://eyes.nasa.gov/apps/earth/
- NASA Earth Observatory: https://earthobservatory.nasa.gov/
- NASA Image and Video Library: https://images.nasa.gov/

### Temperature data and visualization
- NASA GISTEMP: https://data.giss.nasa.gov/gistemp/
- NASA Global Temperature Anomalies 1880–2025 (SVS): https://svs.gsfc.nasa.gov/5603/
- NASA Climate Spiral: https://svs.gsfc.nasa.gov/5190/
- EIC Global Temperature: https://earth.gov/sealevel/vital-signs/global-temperature/
- NASA GISS temperature animations: https://data.giss.nasa.gov/gistemp/animations/index.html

### Sonification and accessibility
- NASA data sonifications: https://www.nasa.gov/data-sonifications/
- NASA Chandra sonification: https://chandra.si.edu/sound/
- W3C keyboard accessibility: https://www.w3.org/WAI/WCAG22/Understanding/keyboard.html
- W3C ARIA slider pattern: https://www.w3.org/WAI/ARIA/apg/patterns/slider/
- W3C WCAG guidance: https://www.w3.org/WAI/standards-guidelines/wcag/

### Attribution and reuse
- NASA media usage: https://www.nasa.gov/nasa-brand-center/images-and-media/
- NASA SVS: https://svs.gsfc.nasa.gov/
- NASA GISS citation guidance: https://data.giss.nasa.gov/gistemp/

---

## 13. Current status

**Status:** concept and UX direction documented; no implementation or dataset validation has been completed.  
**Next team decision:** read the full challenge resources, confirm event start rules, and validate that the chosen EIC visualization and GISTEMP series can be paired accurately.


