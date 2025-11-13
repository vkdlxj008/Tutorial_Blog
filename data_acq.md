---
layout: page
title: "Piano vs Orchestra Album Trends in the U.S. (1900–2020)"
permalink: /data_acq/
---

# 🎵 Piano vs Orchestra Album Trends in the U.S. (1900–2020)

## 🧠 Research Question
How has the balance between piano-related and orchestra-related classical album production in the United States evolved between 1900 and 2020?

---

## 🎯 Project Overview
This post presents my STAT 251 Data Curation project, which curates an original dataset using the **MusicBrainz WS/2 API**.  
The goal is to explore how **piano-centered** and **orchestra-centered** classical recordings have changed over time in the U.S.

The project consists of three stages:
1. **Data Curation:** Fetching U.S. classical albums (1900–2020) via API  
2. **Classification:** Grouping albums into `PianoSolo`, `Orchestra`, `Hybrid`, and `Unknown`  
3. **Analysis & Visualization:** Identifying long-term recording trends by decade

---

## 📦 Data Collection

**Source:** [MusicBrainz API](https://musicbrainz.org/doc/Development/XML_Web_Service/Version_2)

- Queried all U.S. *album-type* releases tagged as “classical”
- Filtered for titles containing piano- or orchestra-related terms
- Saved raw and processed data in `/data/`
- Used a 1.2-second delay between requests to respect API rate limits

**Sample of Collected Data**

| rg_id | title | release_title | year | genre_type |
|-------|--------|---------------|------|-------------|
| e1e06c82-... | *Classical Music for People Who Hate Classical Music* | Same | 2001 | Piano |
| e55cdbb0-... | *Piano Concerto No. 3 / Solo Piano Works* | Same | 2000 | Piano |
| 0eaae045-... | *Classical Piano Collection* | Same | 2005 | Piano |

---

## 🧮 Data Refinement
Using a refined keyword model, albums were further classified as:

- **PianoSolo:** Piano or related solo works (e.g., *Etudes*, *Preludes*, *Nocturnes*)
- **Orchestra:** Works emphasizing orchestral instrumentation (*Symphony*, *Suite*, *Requiem*)
- **Hybrid:** Albums mentioning both piano and orchestra (e.g., *Piano Concertos*)
- **Unknown:** Classical albums without identifiable instrumentation keywords

**Sample after classification**

| title | year | genre_refined |
|-------|------|---------------|
| *Classical Music for People Who Hate Classical Music* | 2001 | Unknown |
| *Piano Concerto No.3 / Solo Piano Works* | 2000 | Hybrid |
| *Classical Piano Collection* | 2005 | PianoSolo |

---

## 📈 Exploratory Data Analysis (EDA)

### 1️⃣ Decade Trends by Genre
<img src="/Tutorial_Blog/blog/hybrid_decade_counts.png" alt="Decade by Genre" width="80%">

> The **1980–2000** period marks a surge in both *PianoSolo* and *Hybrid* albums,  
> likely due to advances in digital recording and renewed interest in solo performance.

---

### 2️⃣ Share of Piano-Related Albums
<img src="/Tutorial_Blog/blog/hybrid_piano_share.png" alt="Piano Share" width="80%">

> Piano-related recordings account for roughly **70–90%** of all classical albums between 1970 and 2000,  
> suggesting a clear emphasis on piano works in modern recording culture.

---

### 3️⃣ Total Album Output by Decade
<img src="/Tutorial_Blog/blog/hybrid_total_albums.png" alt="Total Albums" width="80%">

> Overall album production grows steadily through the late 20th century,  
> reflecting the expansion of recording technology and classical archives.

---

## 🧩 Key Findings
- Piano-related recordings (Solo + Hybrid) **dominate** modern classical output after 1970  
- Orchestra-only albums remain steady but represent a smaller proportion of releases  
- Early 20th-century data is sparse due to incomplete metadata  
- The **1980–2000 digital era** shows peak recording activity for both soloists and orchestras

---

## 💡 Interpretation
These trends align with the historical development of recording media:
- 1950–70s: Rise of **LPs and stereo recordings** enabled large orchestral works  
- 1980–2000: **Digital and CD era** revived solo performance recordings  
- 2000s–present: Decline due to **streaming and metadata inconsistencies**

In short, the spotlight of U.S. classical recording gradually shifted from the concert hall to the solo piano.

---

## ⚙️ Technical Notes
- **Language:** Python (requests, pandas, matplotlib)  
- **Data Source:** MusicBrainz (CC0 License)  
- **Pipeline:** `source/run_pipeline.py` automates collection → classification → aggregation  
- **Visualization:** Generated via `/notebooks/eda.ipynb`

---

## ✍️ Author
**Jun Kim** — STAT 386 Data Curation Project  
[GitHub Repository](https://github.com/vkdlxj008/musicbrainz_API_scraping)

