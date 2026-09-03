---
layout: default
title: "Security engineering at Randori, and VNTA Group"
description: >
  Security engineering at Randori, an IBM company, founding VNTA Group, and
  earlier internships at Dell Technologies and Brown Thomas Arnotts.
permalink: /work/
ventures:
  - name: VNTA Group
    meta: "vnta.xyz · Holding company. One brand at a time"
    url: https://vnta.xyz
    ext: true
    mark: /assets/img/marks/vnta.png
  - name: Vendr
    meta: "vendr.ie · A modern vending platform: curation, infrastructure, data · since January 2026"
    url: https://vendr.ie
    ext: true
    mark: /assets/img/marks/vendr.png
  - name: Éirvox
    meta: "eirvox.ie · Verification led enthusiast commerce, with DRIVE as its editorial layer · since October 2025"
    url: https://eirvox.ie
    ext: true
    mark: /assets/img/marks/eirvox.png
  - name: Maison Seul
    meta: "maisonseul.com · Restraint, form, cultural permanence. Built for longevity, not velocity · since July 2025"
    url: https://maisonseul.com
    ext: true
clients:
  - name: BUILDT
    meta: "buildt.ie · Custom gaming and creator machines, repairs and diagnostics, Dublin"
    url: https://buildt.ie
    ext: true
  - name: EZGO Autoworks
    meta: "ezgoautoworks.ie · A full service garage: servicing, repairs and diagnostics, Ireland"
    url: https://ezgoautoworks.ie
    ext: true
volunteering:
  - name: Dell Technologies
    meta: "TecKno.dell.com content, EMEA intern onboarding panel, Transition Year mentor · 2022"
    url: https://teckno.dell.com
    ext: true
    mark: /assets/img/marks/dell.png
  - name: CSinc.ie, TU Dublin
    meta: "Computer Science Inclusive: camps, workshops and teacher CPD · 2022"
    url: https://csinc.ie
    ext: true
# The old standalone volunteering page. Its content lives here now.
redirect_from:
  - /volunteering/
---

# Work

Security engineering at Randori, and the ventures I run alongside it. Ordered
by what I spend time on, not strictly by date.
{:.lede}

<div class="entry" markdown="1">

<img class="entry-mark" src="/assets/img/marks/ibm.png" alt="IBM" width="26" height="26" loading="lazy" decoding="async">

Randori, an IBM company · Ireland · January 2024 to present
{:.when}

## Security Engineer
{:#ibm}

Randori is an attack surface management product, part of IBM's QRadar suite. I
work on the detection side of it and on the tooling around it, as the sole
Ireland based engineer on the team.

* Build Python CLI tooling and MCP based agent workflows that streamline
  detection and targeting, plus scripts that automate data collection.
* Write regex rules that fingerprint software, services and versions, then
  correlate what is found against known vulnerabilities through CPE mappings.
* Develop detection rules independently, improving customer security posture.
* Identify attack vectors such as exposed login fields, directory listings and
  default installations, and recommend mitigations.
* Support customer and sales teams with technical troubleshooting.

Also volunteered on the Dublin Lab Social and Technical Events Board.

</div>

<div class="entry" markdown="1">

<img class="entry-mark" src="/assets/img/marks/vnta.png" alt="VNTA Group" width="26" height="26" loading="lazy" decoding="async">

VNTA Group · Dublin · November 2024 to present
{:.when}

## Founder
{:#vnta-group}

Vantanéant International Ltd, an Irish registered holding company building and
guiding premium brands through strategy, design systems and long term
direction. Three houses sit under it, each with its own name, system and brand
book. A house that only works while we are standing in it is not a house, so
each is built to be handed the keys.

{% include group.html rows=page.ventures %}

We take residence inside one brand at a time, set direction, build the system
underneath it, then hand over the keys. Current clients:

{% include group.html rows=page.clients %}

</div>

<div class="entry" markdown="1">

<img class="entry-mark" src="/assets/img/marks/dell.png" alt="Dell Technologies" width="26" height="26" loading="lazy" decoding="async">

Dell Technologies, Limerick · February to August 2022
{:.when}

## Cybersecurity Intern
{:#dell}

A six month remote placement in Dell's Security and Resiliency Organization:
alert
monitoring, incident triage, vulnerability scanning and patch prioritisation.
Wrote a LinkedIn article and video about the internship with eight practical
tips for incoming interns.

</div>

<div class="entry" markdown="1">

Brown Thomas Arnotts, Dublin · Summer 2021
{:.when}

## Database Engineering Intern
{:#brown-thomas-arnotts}

Built and maintained SQL databases for retail operations and reporting,
including data integrity, backup and access control processes.

</div>

Volunteering
{:.label}

{% include group.html rows=page.volunteering %}
