---
tags: 🐸
---

# Architecture Diagram

The following is a basic architecture diagram for the refresh Frog & Pencil web platform.

```plantuml
node "Azure Data Storage" as ADS {
[Azure Blob Storage] as ABS
[Azure SQL Managed Service] as ASMS

note top of ABS
	Used to store Page metadata, images
	and minified JS/CSS resources.
end note

note top of ASMS
	Used to store F&P FY data.
end note

ABS -[hidden]d-> ASMS
}


node "Azure Web" as AW {
[Azure CDN] as ACDN
[Frog & Pencil Web] as FPW
[Frog & Pencil Admin] as FPA
}

ADS -[hidden]-> AW
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