# Component Diagrams
## Overview
```mermaid
graph LR

client{Client}

gw[API Gateway]
auth[Authorization Server]
auto_group[Module Autoscaling Group*]
db[DB]

client -->|JWT| gw
gw -->|JWT</br>Validation| auth
auth -.->gw
gw -->|0..*| auto_group
auto_group --> db


```
## Modules
```mermaid
graph LR

account[Account / IAM]
storage[Storage]
content[Content]
comm[Communication]
notif[Notification]

account -...->notif
content -...-> account & storage & notif
comm -...-> account & storage & notif
```



## *Module Autoscaling Group

Each module is individually scalable. The actual scaling functionality depends on the actual deployment instrastructure, for example AWS ECS / EC2 or Kubernetes horizontal pod autoscaling (HPA).

Common social network modules would include:

- **Account / IAM** (Users)
- **Storage** (Files, including images and videos with streaming)
- **Content** (Posts, Comments & Reactions)
- **Communication** (Direct Messages & Group Chat)
- **Notification**

Each module connects to a standalone DB instance or standalone schema within the same DB instance.

## Source Code

> 💡 See raw Markdown above

