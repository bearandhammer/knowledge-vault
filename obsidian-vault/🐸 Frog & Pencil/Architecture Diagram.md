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
	

```plantuml
<style>
component {
	BackgroundColor #b487e8
	LineThickness 1
	LineColor black
}
cloud {
	BackgroundColor #d8e887
	LineThickness 1
	LineColor black
}
database {
	BackgroundColor #87b2e8
	LineThickness 1
	LineColor black
}
storage {
	BackgroundColor #87e8c4
	LineThickness 1
	LineColor black
}
</style>

storage "Azure Blob Storage" as ABS {
}

database "Azure SQL MS" as ASMS {
}

circle Request as REQ

component "F&P Web" as FPW {
}

cloud "Cloudflare" as CF {
}

component "F&P Admin" as FPA {
}

component "Identity Server" as IS {
}

cloud "Azure CDN" as ACDN {
}

note top of ABS  
    Store page meta, images and resources.
end note

note bottom of FPW  
    Frog & Pencil core site. Using
    Blazor, TypeScript, Bulma. 
end note

note bottom of FPA
    Frog & Pencil admin site. Using
    Blazor, TypeScript, Bulma, ChartJS.
end note

note top of ASMS
    FY data and Identity Server.
end note

note right of ACDN
    Serves content at the 'edge'.
end note

ABS <--> ACDN
ABS <--> FPA
ACDN <--> FPW
ACDN <--> FPA
ASMS <--> FPA
FPA <--> CF
CF <--> FPW
REQ <--> CF
FPA <--> IS
FPW <--> IS

CF -[hidden]d-> REQ
FPA -[hidden]-> CF
FPW -[hidden]-> CF
```


