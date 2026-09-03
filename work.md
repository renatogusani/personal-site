---
layout: default
title: "Security engineering at IBM, and VNTA Group"
description: >
  Security engineering at IBM on Randori, founding VNTA Group, and earlier
  internships at Dell Technologies and Brown Thomas Arnotts.
permalink: /work/
ventures:
  - name: Vendr
    meta: "vendr.ie · Premium managed vending for workplaces · since January 2026"
    url: https://vendr.ie
    ext: true
    mark: /assets/img/marks/vendr.png
  - name: Éirvox
    meta: "eirvox.ie · Carbon steering wheels, finished in Dublin · since October 2025"
    url: https://eirvox.ie
    ext: true
    mark: /assets/img/marks/eirvox.png
  - name: Maison Seul
    meta: "maisonseul.com · A slower, longevity focused house · since July 2025"
    url: https://maisonseul.com
    ext: true
    mark: /assets/img/marks/maisonseul.png
volunteering:
  - name: Dell Technologies
    meta: "TecKno.dell.com content, EMEA intern onboarding panel, Transition Year mentor · 2022"
  - name: CSinc.ie, TU Dublin
    meta: "Computer Science Inclusive: camps, workshops and teacher CPD · 2022"
# The old standalone volunteering page. Its content lives here now.
redirect_from:
  - /volunteering/
---

# Work

Security engineering at IBM, and the ventures I run alongside it. Ordered by
what I spend time on, not strictly by date.
{:.lede}

<div class="entry" markdown="1">

IBM, Ireland · January 2024 to present
{:.when}

## Security Engineer, Randori
{:#ibm}

Randori is IBM's attack surface management product, part of the QRadar suite. I
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

Dublin · November 2024 to present
{:.when}

## Founder, VNTA Group
{:#vnta-group}

Vantanéant International Ltd, an Irish registered holding company and brand
studio. I lead strategy, brand and
operations across the group, building shared infrastructure so each company
scales on common foundations while keeping its own identity.

{% include group.html rows=page.ventures %}

</div>

<div class="entry" markdown="1">

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
