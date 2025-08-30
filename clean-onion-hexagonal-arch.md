# Clean Architecture / Onion Architecture

They are layers responsible for organizing the logic of our application.

* **Domain**
* **Use Cases** (domain logic, entities)
* **Adapters** (adapt the information bidirectionally, client-server)
* **External** (e.g., a service like an API)

The adapter is used to separate concerns; it separates the domain logic (which we satisfy through use cases). If we need something external, we adapt it so that the communication with the outside is controlled.

In other words, we use an API (external layer), adapt the data we send bidirectionally through the adapter (adapters layer), and the use case will use the mapped and adapted data.

The adapter is important because if the API changes to another one or the same API is modified in the future, it wouldn’t break the app.

<img width="1280" height="720" alt="Clean architecture" src="https://github.com/user-attachments/assets/42777027-5375-4ac4-a4d9-c45bab1417af" />

# Hexagonal Architecture

Think of it more as port and adapter architecture instead of hexagonal...

* **Services** (this is where the domain layer is)
* **Ports**
* **Adapters**
* **External** (the external layer can be another service or another technology like a database) (and that service also has its own input and output ports)

Services (each of these services will satisfy business logic). Each service will have ports that limit what enters or leaves the service; it’s like an interface.

Adapters (adapters implement the ports).

The service can be thought of as a clean architecture.

<img width="1280" height="720" alt="hexagonal" src="https://github.com/user-attachments/assets/9f3ded31-03ce-4199-aaa9-c106d5b7dcc3" />

# ADVICE

When working with architectures, patterns, or anything else, you need to know how to adapt it to what you need. For example, we might need a hybrid, or we might not need 100% of clean, onion, or hexagonal architecture.

**What’s important is:**

* Knowing what we really need.
* Knowing the tools we have (advantages/disadvantages).

Then, based on that, adapt the design of the architecture.

# DETAILS

The **frontend or UI** is really an **external layer**, because everything external is removable.

The **DOM** is really an adapter; it’s an API we use to communicate with the browser. So, if the browser updates in the future, communication doesn’t break, only the adapter changes. It’s just a way to communicate.

**Entity** is typically a class or object that models a **domain concept**, holding data (state) and behavior (methods), and has a unique identity. It is not an interface, function, or simple variable. A **domain** can have multiple **entities**, each representing a distinct real-world concept, for example, in the domain of an e-commerce, entities would be **User**, **Product**, **Order**, and **Payment**. Real example:

```ts
abstract class BaseEntity {
  constructor(
    public readonly id: number,
    public readonly createdAt = new Date()
  ) {}
}

class User extends BaseEntity {
  constructor(id: number, public name: string, public email: string) {
    super(id);
  }
}

class Product extends BaseEntity {
  constructor(
    id: number,
    public name: string,
    public price: number,
    public stock: number
  ) {
    super(id);
  }
}

class Order extends BaseEntity {
  public readonly total: number;

  constructor(id: number, public user: User, public products: Product[]) {
    super(id);
    this.total = products.reduce((sum, p) => sum + p.price, 0);
  }
}

class Payment extends BaseEntity {
  constructor(
    id: number,
    public order: Order,
    public amount: number,
    public method: 'card' | 'paypal',
    public readonly paidAt = new Date()
  ) {
    super(id);
  }
}
