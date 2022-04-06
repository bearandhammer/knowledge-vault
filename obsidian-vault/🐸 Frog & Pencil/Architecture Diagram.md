---
tags: 🐸
---

# Architecture Diagram

The following is a basic architecture diagram for the refresh Frog & Pencil web platform.

```plantuml
package "Data Storage" {
[Azure Blob Storage] as ABS
[Azure SQL Managed Service]

note left of ABS
	Used to store Page metadata 
	and minified JS/CSS resources.
end note

}
```

package "Some Group" {
  HTTP - [First Component]
  [Another Component]
}

node "Other Groups" {
  FTP - [Second Component]
  [First Component] --> FTP
}

cloud {
  [Example 1]
}


database "MySql" {
  folder "This is my folder" {
    [Folder 3]
  }
  frame "Foo" {
    [Frame 4]
  }
}


[Another Component] --> [Example 1]
[Example 1] --> [Folder 3]
[Folder 3] --> [Frame 4]