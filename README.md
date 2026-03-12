# Microservices Lab - Event Driven Architecture with Kafka (KRaft Mode)

## Architecture
Client → API Gateway (8080) → Order Service (8081) → Kafka → Inventory Service (8082) + Billing Service (8083)

## How to Run

### 1. Start Kafka
docker-compose up -d

### 2. Start Services (4 separate terminals)
cd order-service && ./mvnw spring-boot:run
cd inventory-service && ./mvnw spring-boot:run
cd billing-service && ./mvnw spring-boot:run
cd api-gateway && ./mvnw spring-boot:run

### 3. Test in Postman
POST http://localhost:8080/orders
Content-Type: application/json

{
    "orderId": "ORD-1001",
    "item": "Laptop",
    "quantity": 1
}

## Expected Output
- Postman: "Order Created & Event Published"
- Inventory terminal: "Inventory Updated for Order: ..."
- Billing terminal: "Invoice Generated for Order: ..."

