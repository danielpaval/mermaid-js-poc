# Sequence Diagram
## Order a ride

```mermaid
sequenceDiagram
autonumber

actor User
participant OS as Order Service
participant LS as Location Service
participant RS as Routing Service
participant DS as Driver Service
actor Driver

User->>OS: Order a ride
activate OS

alt is new pickup address
    OS->>LS: Validate & geocode pickup addr.<br/> incl. mobile dev. loc.
    activate LS
    LS-->>OS: Validated pickup addr. and location
    deactivate LS
end

par 1. driver
	OS->>DS: Determine driver for pickup & ride
    activate DS
    Note left of DS: Based on proximity,<br/>round robin balancing, etc.
    loop until a driver accepts or the order times out
        DS->>Driver: Ask to accept ride
        activate Driver
        alt
            Driver-->>DS: Accept ride
        else
            Driver-->>DS: Reject ride
        end
        deactivate Driver
        DS-->>OS: Recommended driver
    end
    deactivate DS    
and 2. destination address & route
	alt is new destination address
        OS->>LS: Validate & geocode dest. addr.
        activate LS
        LS-->>OS: Validated dest. addr. and location
        deactivate LS
    end
    OS->>RS: Determine best route between pickup and dest. addresses
    activate RS
    RS-->>OS: Recommended route
    deactivate RS
end
OS->>User: Ride ordered

deactivate OS
```
### Notes
- For the sake of having a diverse sequence diagram, geocoding a new pickup address is performed when placing a ride order although it would usually be handled prior to that (just like with saved addresses). Geocoding (both for pickup and destination) would be cached for already saved addresses.
- For the sake of showcasing parallel execution, the destination address is validated and geocoded at the same time that a nearby driver is looked up for picking the rider

### Source Code

```mermaid-example
sequenceDiagram
autonumber

actor User
participant OS as Order Service
participant LS as Location Service
participant RS as Routing Service
participant DS as Driver Service
actor Driver

User->>OS: Order a ride
activate OS

alt is new pickup address
    OS->>LS: Validate & geocode pickup addr.<br/> incl. mobile dev. loc.
    activate LS
    LS-->>OS: Validated pickup addr. and location
    deactivate LS
end

par 1. driver
	OS->>DS: Determine driver for pickup & ride
    activate DS
    Note left of DS: Based on proximity,<br/>round robin balancing, etc.
    loop until a driver accepts or the order times out
        DS->>Driver: Ask to accept ride
        activate Driver
        alt
            Driver-->>DS: Accept ride
        else
            Driver-->>DS: Reject ride
        end
        deactivate Driver
        DS-->>OS: Recommended driver
    end
    deactivate DS    
and 2. destination address & route
	alt is new destination address
        OS->>LS: Validate & geocode dest. addr.
        activate LS
        LS-->>OS: Validated dest. addr. and location
        deactivate LS
    end
    OS->>RS: Determine best route between pickup and dest. addresses
    activate RS
    RS-->>OS: Recommended route
    deactivate RS
end
OS->>User: Ride ordered

deactivate OS
```