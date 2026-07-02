# CIN and CLA Pathways

Tracing the statutory children's social care pathway in England - **referral → assessment → Child in Need (CIN) → Child Protection Plan (CPP) → Children Looked After (CLA)** - using the Department for Education's published child-level census data.

A companion piece to an earlier SEN (Special Educational Needs) pathways notebook, using the same approach: pull DfE's own local-authority-level statistics, join them along a pathway, and see what the funnel actually looks like across years and local authorities.

## Why this project

Another "conversation with the wife" inpired project, this started as a follow-on from SEN pathways work, but chose deliberately to work in the CIN/CLA space because it overlaps directly with my wife's career in child protection social work - CIN, CLA, and category-of-need terminology are her day-to-day working vocabulary. The goal is a project that's both technically defensible (real public data, real joins, real data-quality problems to solve) and substantively meaningful to someone who actually works in the field.

## Data sources

All data is published by the Department for Education via [Explore Education Statistics](https://explore-education-statistics.service.gov.uk/), under the Open Government Licence.

| Stage | Dataset | Collection |
|---|---|---|
| Referral | C1: Referrals and re-referrals to children's social care services by local authority | Children in Need census |
| Assessment | C2: Completed assessments by duration and local authority | Children in Need census |
| CIN / CPP | Characteristics of children in need | Children in Need census |
| CLA | CLA numbers and rates per 10,000 children by local authority | SSDA903 (Children Looked After) collection |
| CLA characteristics | CLA on 31 March by characteristics (legal status, primary need, placement type) | SSDA903 (Children Looked After) collection |

Data is pulled directly from DfE's data-catalogue CSV endpoints (see the notebook for exact URLs).

## A known data-quality problem, kept deliberately visible

Local authority boundaries changed mid-series:
- Northamptonshire split into North and West Northamptonshire (April 2021)
- Cumbria split into Westmoreland and Furness, and Cumberland (April 2023)
- Dorset, Bournemouth, and Poole merged into Bournemouth, Christchurch and Poole, and Dorset (April 2019)

Any local-authority-level time trend has to handle these splits explicitly rather than silently dropping or misattributing rows. This is treated as a feature of the analysis, not a nuisance to filter out.

## Scope note: Emergency Protection Orders

This notebook stops at CLA. Emergency Protection Orders are made by the family court and recorded by Cafcass, not the Department for Education - they sit outside the Children in Need census and the SSDA903 collection entirely. Rather than forcing a join to a dataset that doesn't align cleanly, the final section of the notebook documents where the publicly available statutory pathway data actually stops.

## Setup

```bash
pip install -r requirements.txt
jupyter notebook cin_cla_pathways.ipynb
```

## Status

Work in progress - starting with data loading and inspection, building out the pathway joins next.
