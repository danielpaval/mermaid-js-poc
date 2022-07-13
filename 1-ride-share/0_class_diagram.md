# Class Diagram
```mermaid
classDiagram
direction TB

class User {
	id
	name
}
class Driver {
	licenseNumber
}
class Car {
	id
    plateNumber
    model
}
class Order {
	id
}
class Address {
	id
    line1
    line2
    city_id
    region_id
    country_id
    geocode
}

Driver --|> User
Driver --> "0..*" Car
User -- "0..*" Order
User o-- "0..*" Address: savedAddresses
Order o-- Address: pickupAddress
Order o-- Address: destinationAddress
```

## Notes

Actual ride sharing platforms are very similar, but also might differ in various aspects. This is more of a theoretical approach that relies on the following notes and assumptions:

- Drivers might either own or otherwise be able to use multiple cars

## Source Code

> 💡 See raw Markdown above
