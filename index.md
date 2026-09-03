---
layout: default
home: true
title: Renato Gusani
description: >
  Security engineer at Randori, an IBM company, building Python and MCP tooling
  for attack surface management. Founder at VNTA Group. Dublin, Ireland.
permalink: /
now:
  - name: Randori
    meta: "An IBM company · Security Engineer, since January 2024"
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
    meta: Randori, VNTA Group, and what came before
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
  <p class="home-tagline">Security Engineer at Randori, an IBM company. Founder at VNTA Group. Dublin, Ireland.</p>
</header>

I build Python automation and detection logic for attack surface management at
Randori, an IBM company, on the product that carries its name. Most of what I
ship is tooling: CLI utilities, MCP servers and agent integrations.
{:.lede}

Now
{:.label}

{% include group.html rows=page.now %}

Sections
{:.label}

{% include group.html rows=page.sections %}

{% include socials.html %}
