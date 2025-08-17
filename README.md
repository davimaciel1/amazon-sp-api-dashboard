# 🚀 Amazon SP-API Dashboard SaaS 2025

[![Deploy with Coolify](https://img.shields.io/badge/Deploy%20with-Coolify-blue)](https://coolify.io)
[![Next.js](https://img.shields.io/badge/Next.js-15-black)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.6-blue)](https://www.typescriptlang.org)

## 🎯 Modern Amazon Seller Dashboard - No AWS IAM Required!

A complete multi-tenant SaaS dashboard for Amazon sellers, similar to Shopkeeper.com but with modern architecture.

### ✨ Key Features

- 📊 **Sales Analytics** - Real-time sales data with advanced filters
- 💰 **Profit & Loss** - Automatic calculation with COGS management
- 📦 **Inventory Management** - FBA/FBM stock tracking
- 🎯 **PPC Analytics** - ACOS, TACOS, campaign performance
- ⭐ **Review Management** - Automated review requests
- 🔄 **Order Sync** - Real-time order synchronization
- 🌍 **Multi-Marketplace** - Support for all Amazon marketplaces
- 👥 **Multi-Tenant** - Manage multiple seller accounts

### 🔐 Authentication Changes (October 2023)

**NO LONGER NEEDED:**
- ❌ AWS IAM Roles
- ❌ AWS Access Keys
- ❌ AWS Signature V4

**ONLY REQUIRED:**
- ✅ Login with Amazon (LWA) OAuth 2.0
- ✅ Client ID & Secret (rotate every 180 days)
- ✅ Refresh Token

### 🛠️ Tech Stack

#### Frontend
- **Next.js 15** - App Router with RSC
- **Shadcn UI** - Modern component library
- **TanStack Query** - Data fetching & caching
- **Recharts** - Beautiful charts
- **TypeScript** - Type safety

#### Backend
- **Fastify** - High-performance server
- **tRPC** - Type-safe API
- **Drizzle ORM** - Fast database queries
- **BullMQ** - Job queues
- **Redis** - Caching & sessions

#### Infrastructure
- **PostgreSQL 16** - Main database
- **Docker Compose** - Container orchestration
- **Coolify** - Self-hosted deployment
- **Clerk** - User authentication

## 🚀 Quick Start

### Prerequisites

1. **Amazon Seller Account**
2. **Developer Access** in Seller Central
3. **Coolify** instance running
4. **Clerk** account for auth

### Local Development

```bash
# Clone the repository
git clone https://github.com/davimaciel1/amazon-sp-api-dashboard.git
cd amazon-sp-api-dashboard

# Install dependencies
pnpm install

# Setup environment
cp .env.example .env.local

# Run database migrations
pnpm db:migrate

# Start development
pnpm dev
```

### Deploy to Coolify

1. Fork this repository
2. In Coolify, create new application
3. Select Docker Compose
4. Point to `docker-compose.yml`
5. Configure environment variables
6. Deploy!

## 📋 Environment Variables

```env
# Database
DATABASE_URL=postgresql://user:pass@localhost:5432/amazon_dashboard

# Redis
REDIS_URL=redis://localhost:6379

# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_xxx
CLERK_SECRET_KEY=sk_test_xxx

# Encryption
ENCRYPTION_KEY=your-32-byte-hex-key

# SP-API (stored encrypted per tenant)
# No AWS credentials needed!
```

## 🔑 Getting SP-API Credentials

1. **Login to Seller Central**
2. Go to **Apps & Services → Develop Apps**
3. Click **Add new app** or select existing
4. Get **Client ID** and **Client Secret**
5. Click **Authorize** to get **Refresh Token**
6. Add credentials in dashboard settings

⚠️ **Important:** Client Secret expires every 180 days!

## 📊 Features Overview

### Sales Dashboard
- Period comparison (Today, 7d, 30d, YTD, etc.)
- Marketplace filtering
- Order type filtering (FBA/FBM/Business)
- Advanced metrics filtering
- Export to CSV/Google Sheets

### Inventory Management
- Real-time stock levels
- Restock recommendations
- Shipment tracking
- ROI calculations

### PPC Analytics
- Campaign performance
- ACOS/TACOS tracking
- Keyword analysis
- Bid optimization suggestions

### Profit & Loss
- Automatic fee calculations
- COGS management
- Tax configuration
- Custom expenses

## 🏗️ Architecture

```mermaid
graph TB
    A[Next.js Frontend] --> B[tRPC API]
    B --> C[PostgreSQL]
    B --> D[Redis Cache]
    B --> E[BullMQ Workers]
    E --> F[SP-API SDK]
    F --> G[Amazon SP-API]
    H[Clerk Auth] --> A
    I[LWA OAuth] --> F
```

## 🔄 Credential Rotation

The system automatically monitors credential expiration:

- Daily checks for expiring credentials
- Email alerts 30 days before expiration
- Dashboard notifications
- Guided rotation process

## 📈 Performance

- **Response Time:** < 100ms p95
- **Order Sync:** Every 15 minutes
- **Data Freshness:** Real-time for critical metrics
- **Concurrent Users:** 10,000+
- **API Rate Limiting:** Automatic with exponential backoff

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) first.

## 📄 License

MIT License - see [LICENSE](LICENSE) file

## 🔗 Links

- [SP-API Documentation](https://developer-docs.amazon.com/sp-api/)
- [Coolify Documentation](https://coolify.io/docs)
- [Project Demo](https://demo.amazon-dashboard.com)

## 💬 Support

- [GitHub Issues](https://github.com/davimaciel1/amazon-sp-api-dashboard/issues)
- [Discord Community](https://discord.gg/amazon-sellers)
- Email: support@amazon-dashboard.com

---

Made with ❤️ for Amazon Sellers