---
layout: home
title: Home
description: DASH Webinars
nav_order: 1
---

{%- assign workshops = site.pages 
    | where_exp: "item", "item.grand_parent == null"
    | where_exp: "item", "item.parent == null"
    | sort: "title" 
-%}

<img src="assets/img/DASH Series.png" alt="Workshop Title Slide" width="720">

# Welcome to DASH: The Data Analysis Support Hub Webinars

DASH workshops help registrants with data analysis and visualization by providing training for software programs and coding languages including Excel, LaTeX, Python, R, and SPSS.

DASH workshops welcome students, staff, and faculty from any discipline, as well as the public at large. A number of DASH workshops are also geared towards beginners, so even if you’re new to data analysis, we encourage you to sign up and learn!

## 2022-2023 DASH Workshop Topics

<div markdown="1" style="border: 1px solid #7a003c; border-radius: 6px; margin-bottom: 1em; padding: 0.5em 1em 0; margin-top: 1em;" class="toc">
<summary style="cursor:default; display: block; border-bottom: 1px solid #302d36; margin-bottom: 0.5em">
  Workshops
</summary>
<ul>
{% for workshop in workshops %}
{% if workshop.title != null and workshop.title != "Home" and workshop.title != "Learn More" %}
<li><a href="{{workshop.url | absolute_url}}">{{workshop.title}}</a></li>
{% endif %}
{% endfor %}
</ul>
</div>

## Collaborations and Co-Sponsored Events
DASH collaborates with the Do More with Digital Scholarship and Research Data Management workshop series on certain events. Access recordings of [DMDS events](https://scds.github.io/dmds-22-23/Intro.html) and [RDM Webinars](https://scds.github.io/intro-rdm/). 

**2022-2023 DMDS Collaborations**
- What is Digital Scholarship? 
- Network Visualizations with Gephi
- Visualizing Texts with Voyant Tools
- How to Lie with Data
- Sound Data
- Computational Approaches to Text Preparation and Analysis

**2023 RDM Collaboration**
- Qualitative Data
