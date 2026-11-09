# Swapora Backend

Express.js API server for the Swapora P2P marketplace.

## Tech Stack

- **Runtime**: Node.js 20+
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL
- **Cache/Queue**: Redis (BullMQ)
- **Blockchain**: Stellar SDK (Soroban contracts)
- **Payments**: Paystack integration
- **SMS**: Termii API

## Quick Start

### Prerequisites

- Node.js 20+
- PostgreSQL 16+
- Redis 7+
- pnpm (or npm)

### Installation

```bash
# Install dependencies
npm install

# Copy environment file
cp .env.example .env
# Edit .env with your configuration

# Run migrations
npm run db:migrate

# Start development server
npm run dev
```

Server runs on `http://localhost:3001`

### Available Scripts

- `npm run dev` - Start development server with hot reload
- `npm run build` - Build for production
- `npm start` - Start production server
- `npm test` - Run test suite
- `npm run lint` - Type check with TypeScript
- `npm run db:migrate` - Run database migrations
- `npm run db:migrate:rollback` - Rollback last migration

## Environment Variables

See `.env.example` for all required environment variables. Key variables:

- `DATABASE_URL` - PostgreSQL connection string
- `REDIS_URL` - Redis connection string
- `JWT_SECRET` - Secret for JWT tokens
- `ESCROW_CONTRACT_ID` - Deployed escrow contract address
- `PAYSTACK_SECRET_KEY` - Paystack API key
- `TERMII_API_KEY` - Termii SMS API key

## API Documentation

Once the server is running, visit:
- Swagger UI: `http://localhost:3001/api-docs`
- Health check: `http://localhost:3001/health`
- Readiness: `http://localhost:3001/ready`

## Project Structure

```
backend/
├── src/
│   ├── middleware/     # Express middleware
│   ├── routes/         # API route handlers
│   ├── services/       # Business logic & external integrations
│   ├── types/          # TypeScript type definitions
│   ├── utils/          # Utility functions
│   ├── db.ts           # Database connection
│   └── index.ts        # Server entry point
├── migrations/         # Database migrations
├── sql/                # SQL schemas
├── Dockerfile          # Production Docker image
└── package.json
```

## Docker

Build and run with Docker:

```bash
docker build -t swapora-backend .
docker run -p 3001:3001 --env-file .env swapora-backend
```

## Testing

```bash
# Run all tests
npm test

# Run with coverage
npm test -- --coverage

# Run specific test file
npm test -- src/routes/trades.test.ts
```

## License

MIT
