---
tags: 🐸
---

# Architecture Diagram

The following is a basic architecture diagram for the refresh Frog & Pencil web platform.

```plantuml
package "Azure Data Storage" as ADS {
[Azure Blob Storage] as ABS
[Azure SQL Managed Service] as ASMS

note top of ABS
	Used to store Page metadata, images
	and minified JS/CSS resources.
end note

note top of ASMS
	Used to store F&P FY data.
end note

ABS -[hidden]> ASMS
}


package "Azure Web" as AW {
[Azure CDN] as ACDN
[Frog & Pencil Web] as FPW
[Frog & Pencil Admin] as FPA

ACDN -[hidden]-> FPW
FPW -[hidden]-> FPA
}

ADS -[hidden]u-> AW
```
