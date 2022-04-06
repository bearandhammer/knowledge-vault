---
tags: 🐸
---

# Architecture Diagram

The following is a basic architecture diagram for the refresh Frog & Pencil web platform.

```plantuml
node "Data Storage" as DS {
[Azure Blob Storage] as ABS
[Azure SQL MS] as ASMS
}

node "Web" as WEB {
[Azure CDN] as ACDN
[F&P Web] as FPW
[F&P Admin] as FPA

ACDN -[hidden]d-> FPA
FPA -[hidden]d-> FPW
}

node "Utility" as UT {
[Cloudflare] as CF
}

DS -[hidden]d-> WEB
WEB -[hidden]r-> UT
```
	

