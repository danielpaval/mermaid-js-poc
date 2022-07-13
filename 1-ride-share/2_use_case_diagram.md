# Use Case Diagram
There doesn't seem to be a native use case diagram syntax in Mermaid.js, but one may be *emulated* using a regular graph diagram:
```mermaid
graph LR

user{User}
driver{Driver}

order([Order a ride])
accept([Accept a ride])
pickup([Pickup from address])
ride([Ride to destination])
pay([Process payment])

order -..->|include| accept & pickup
pay -..->|include| ride

user --- order & pickup & ride & pay
driver --- accept & pickup & ride

subgraph App
 	order
 	accept
 	pickup
 	ride
 	pay	
end
```

> 💡 Except for sequence diagrams that are quite unabiguous when it comes to layout, any text-based diagraming tool will more or less strugle to optimally and *automatically* render the graph-like layout of other diagram types. While, for example, PlantUML might accept some layout hints, Mermaid.js appears to be even less flexible and is only able to put together the unimpressive (to say the least) diagram above.

## Source Code

```mermaid-example
graph LR

user{User}
driver{Driver}

order([Order a ride])
accept([Accept a ride])
pickup([Pickup from address])
ride([Ride to destination])
pay([Process payment])

order -..->|include| accept & pickup
pay -..->|include| ride

user --- order & pickup & ride & pay
driver --- accept & pickup & ride

subgraph App
 	order
 	accept
 	pickup
 	ride
 	pay	
end
```