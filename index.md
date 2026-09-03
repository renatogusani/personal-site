---
layout: default
home: true
title: Renato Gusani
description: >
  Security engineer at IBM Security, building Python and MCP tooling for attack
  surface management. Founder of VNTA Group. Dublin, Ireland.
permalink: /
now:
  - name: IBM Security
    meta: "Security Engineer, Randori · since January 2024"
    url: /work/#ibm
    mark: /assets/img/marks/ibm.png
  - name: VNTA Group
    meta: "Founder · Vendr, Éirvox, Maison Seul"
    url: /work/#vnta-group
    mark: /assets/img/marks/vnta.png
  - name: SpaceXplorer
    meta: "SpaceX and NASA APOD APIs · 2023"
    url: https://spacexplorer.info
    ext: true
    mark: /assets/img/marks/spacexplorer.png
sections:
  - name: Work
    meta: IBM, VNTA Group, and what came before
    url: /work/
    icon: work
  - name: Projects
    meta: "Vendr, Éirvox, Maison Seul, SpaceXplorer"
    url: /projects/
    icon: projects
  - name: About
    meta: Background, education, and what I care about
    url: /about/
    icon: about
  - name: Contact
    meta: Email, LinkedIn, GitHub, CV
    url: /contact/
    icon: mail
---

<header class="home-head">
  <h1 class="home-name">Renato Gusani</h1>
  <p class="home-tagline">Security engineer at IBM. Founder, VNTA Group. Dublin, Ireland.</p>
</header>

I build Python automation and detection logic for attack surface management on
Randori, part of IBM's QRadar suite. Most of what I ship is tooling: CLI
utilities, MCP servers and agent integrations.
{:.lede}

Now
{:.label}

{% include group.html rows=page.now %}

Sections
{:.label}

{% include group.html rows=page.sections %}

{% include socials.html %}
