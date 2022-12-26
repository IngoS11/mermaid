# Mermaid tutorial

The Mermaid Live Editor can be found at [mermaid.live](https://mermaid.live)

## Entity Relationship Diagram

```mermaid
erDiagram
    Customer ||--o{ Order : places
    Order ||--o{ LineItem : contains
    Customer {
        String id
        String name
    }
    Order {
        String id
        OrderStatus status
    }
    LineItem {
        String code
        String description
        int quantity
        int price
    }
```

## Flowchart Sample

```mermaid
flowchart
    S[Start] --> A[Enter your email];
    A --> B{Existing User?};
    B --> |No| C(Enter name);
    B --> |Yes| E;
    C --> D{Accept conditions?}
    D -->|Yes| E(Send email with link)
    D -->|No| A
```

## Sequence Diagram Sample

Some text in between the diagrams

```mermaid
sequenceDiagram
   participant Client
   participant OAuthProvider
   participant Server
   Client->>OAuthProvider: Request access token
   activate OAuthProvider
   OAuthProvider->>Client: Send access token
   deactivate OAuthProvider
   Client->>Server: Request resource
   activate Server
   Server->>OAuthProvider: Validate token
   activate OAuthProvider
   OAuthProvider->>Server: Token valid
   deactivate OAuthProvider
   Server->>Client: Send resource
   deactivate Server
```

## Class Diagram Sample

```mermaid
classDiagram
   class Order {
      +OrderStatus status
   }
   class OrderStatus {
      <<enumeration>>
      FAILED
      PENDING
      PAID
   }
   class PaymentProcessor {
      <<interface>>
      -String apiKey
      connect(String url, JSON header)
      +processPayment(Order order) OrderStatus
   }
   class Customer {
      +String name
   }
   Customer <|-- PrivateCustomer
   Customer <|-- BusinessCustomer
   PaymentProcessor <|-- StripePaymentProcessor
   PaymentProcessor <|-- PayPalPaymentProcessor
   Order o-- Customer
```
