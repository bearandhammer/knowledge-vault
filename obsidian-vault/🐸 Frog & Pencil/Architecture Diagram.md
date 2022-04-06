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

DS --d-> WEB
WEB --r-> UT
```
	
```plantuml
node Node1 as n1
node "Node 2" as n2
file f1 as "File 1"
cloud c1 as "this
is
a
cloud"
cloud c2 [this
is
another
cloud]

n1 -> n2
n1 --> f1
f1 -> c1
c1 -> c2
```

note top of ABS
	Used to store Page metadata, images
	and minified JS/CSS resources.
end note

note top of ASMS
	Used to store F&P FY data.
end note

node "Azure Data Storage" as ADS {
[Azure S] as ABS
[Azure SQL] as ASMS

ABS -[hidden]d-> ASMS
}


node "Azure Web" as AW {
[Azure C] as ACDN
[Frog P Web] as FPW
[Frog Admin] as FPA

ACDN -[hidden]d-> FPW
FPW -[hidden]d-> FPA
}

ADS -[hidden]d-> AW