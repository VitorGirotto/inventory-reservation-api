# Functionalities

API to solve concurrent sales of the same item. The API will make a reservation
an atomic operation. Either the sale goes through or it fails.

## MVP capabilities

The completed API will support:

- Product creation and consultation.
- Stock adjustments.
- Availability consultation.
- Temporary inventory reservations.
- Reservations containing multiple products.
- Reservation confirmation.
- Reservation cancellation.
- Automatic reservation expiration.
- Protection against overselling.
- Idempotent reservation requests.
- Consistent validation and errors.
- Integration tests against PostgreSQL.
- OpenAPI documentation.
- Docker-based local execution.
- GitHub Actions verification.
- Deployment of a demonstration environment.

## Tech stack

- Node.js
- TypeScript
- Express
- PostgreSQL
- Drizzle ORM
- Drizzle Kit
- Zod
- Vitest
- Supertest
- OpenAPI/Swagger
- Docker Compose
- GitHub Actions
- npm

## Reservation Status

- Active: inventory is currently held.
- Confirmed: reservation became a complete allocation.
- Cancelled: cliente released it.
- Expired: system released after the deadline (15 minutes).

## API Routes

### System

| Method | Route     | Purpose                                 |
| ------ | --------- | --------------------------------------- |
| GET    | `/health` | Confirm that the application is running |
| GET    | `/ready`  | Confirm that the database is reachable  |

### Products

| Method | Route                                 | Purpose                                            |
| ------ | ------------------------------------- | -------------------------------------------------- |
| POST   | `/api/products`                       | Create a product                                   |
| GET    | `/api/products`                       | List products with pagination                      |
| GET    | `/api/products/:id`                   | Retrieve one product                               |
| PATCH  | `/api/products/:id`                   | Update basic product information                   |
| POST   | `/api/products/:id/stock-adjustments` | Increase or decrease physical stock                |
| GET    | `/api/products/:id/availability`      | Return physical, reserved and available quantities |

### Reservations

| Method | Route                                 | Purpose                                            |
| ------ | ------------------------------------- | -------------------------------------------------- |
| POST   | `/api/products`                       | Create a product                                   |
| GET    | `/api/products`                       | List products with pagination                      |
| GET    | `/api/products/:id`                   | Retrieve one product                               |
| PATCH  | `/api/products/:id`                   | Update basic product information                   |
| POST   | `/api/products/:id/stock-adjustments` | Increase or decrease physical stock                |
| GET    | `/api/products/:id/availability`      | Return physical, reserved and available quantities |
