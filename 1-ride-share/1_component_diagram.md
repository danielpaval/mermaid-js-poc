# Component Diagram
There doesn't seem to be a native component diagram syntax in Mermaid.js, but one may be *emulated* using a regular graph diagram:

```mermaid
graph

order[Order Module]
location[Location, Routing & Tracking Module]
account[Account / IAM Module]

order -.-> location & account
location -.-> account
```

> 💡 For simplicity only the high-level module components are represented

## Source Code

```mermaid-example
graph

order[Order Module]
location[Location, Routing & Tracking Module]
account[Account / IAM Module]

order -.-> location & account
location -.-> account
```

