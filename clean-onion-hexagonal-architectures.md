# Clean Architecture / Onion Architecture

They are layers responsible for organizing the logic of our application.

* **Domain**
* **Use Cases** (domain logic, entities)
* **Adapters** (adapt the information bidirectionally, client-server)
* **External** (e.g., a service like an API)

The adapter is used to separate concerns; it separates the domain logic (which we satisfy through use cases). If we need something external, we adapt it so that the communication with the outside is controlled.

In other words, we use an API (external layer), adapt the data we send bidirectionally through the adapter (adapters layer), and the use case will use the mapped and adapted data.

The adapter is important because if the API changes to another one or the same API is modified in the future, it wouldn’t break the app.

# Hexagonal Architecture

* **Services** (this is where the domain layer is)
* **Ports**
* **Adapters**
* **External** (the external layer can be another service or another technology like a database) (and that service also has its own input and output ports)

Services (each of these services will satisfy business logic). Each service will have ports that limit what enters or leaves the service; it’s like an interface.

Adapters (adapters implement the ports).

The service can be thought of as a clean architecture.

# ADVICE

When working with architectures, patterns, or anything else, you need to know how to adapt it to what you need. For example, we might need a hybrid, or we might not need 100% of clean, onion, or hexagonal architecture.

**What’s important is:**

* Knowing what we really need.
* Knowing the tools we have (advantages/disadvantages).

Then, based on that, adapt the design of the architecture.

# DETAILS

The **frontend or UI** is really an **external layer**, because everything external is removable.

The **DOM** is really an adapter; it’s an API we use to communicate with the browser. So, if the browser updates in the future, communication doesn’t break, only the adapter changes. It’s just a way to communicate.
