# Introduction

## Objective

This repo showcases the use of [**Mermaid.js**](https://mermaid-js.github.io/mermaid/#/) for building various UML diagrams in two common architectural scenarios:

- A [**social network**](0-social-network/) platform
- A [**ride share**](1-ride-share/) app

## Mermaid.js

Mermaid.js, similarly to [PlantUML](https://plantuml.com), renders text-based diagram definitions and, thus, may be versioned with Git. However, being a JS-based tool, compared to the latter's Java tech stack, it seems to get a lot more traction recently (for readers in the distant future this means July 2022 😜), maybe due to it being easier to integrate. More, it is widely adopted as `mermaid` code blocks in Markdown including online on GitHub, but also with desktop editors such as [Typora](https://typora.io).

As a quick example:

```mermaid-example
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

Is rendered out-of-the-box as:

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

Note, however, that Mermaid.js might not currently be as feature-rich as the veteran PlanUML, but it allows for custom theming, though not covered here.

### Online Editor

[Online FlowChart & Diagrams Editor - Mermaid Live Editor](https://mermaid.live)