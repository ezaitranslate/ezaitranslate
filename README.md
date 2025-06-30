# EzAITranslate

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-blue)](https://www.typescriptlang.org/)
[![Next.js](https://img.shields.io/badge/Next.js-13+-black)](https://nextjs.org/)

> **Precision Translation Powered by AI**

EzAITranslate is an advanced AI translation platform that leverages cutting-edge language models to provide high-quality translations with customizable domains, tones, and styles. Built for performance, scalability, and SEO optimization.

## 🌟 Key Features

### 🔤 Multi-Platform Translation
- **Smart Text Translation**: High accuracy with context preservation
- **Multi-Language Support**: 100+ languages supported
- **Customizable Output**: Adjust domain, tone, and style
- **Real-time Streaming**: Instant translation results

### 📄 Document Processing
- Support for multiple formats (PDF, DOCX, PPTX, etc.)
- Original formatting preservation
- Batch processing for large documents
- Queue management for document processing

### 🚀 Performance Optimization
- Microservices architecture
- Asynchronous processing with Redis Queue
- Auto-scaling workers based on load
- Translation result caching
- CDN integration for global performance

### 🔒 Security & Compliance
- End-to-end encryption
- GDPR compliance
- No sensitive data storage
- Granular access control
- Secure API authentication

### 📊 SEO & Analytics
- Search engine optimization
- Schema.org markup
- Multi-language sitemap
- Performance analytics
- Usage tracking and insights

## 🛠 Tech Stack

### Backend
- **Node.js** (v18+): Runtime environment
- **Express/Nest.js**: API framework
- **MySQL 8.0+**: Relational database
- **Redis 6.0+**: Cache and message broker
- **PM2**: Process management
- **BullMQ**: Job queue system
- **Jest/Supertest**: Testing framework

### Frontend
- **Next.js 13+**: React framework with App Router
- **TypeScript**: Programming language
- **TailwindCSS**: Utility-first CSS framework
- **i18next**: Internationalization
- **React Query**: Data fetching and caching
- **Framer Motion**: Animation library

### DevOps
- **Docker & Docker Compose**: Containerization
- **GitHub Actions**: CI/CD pipeline
- **Nginx**: Reverse proxy and load balancer
- **PM2**: Production process manager
- **Sentry**: Error monitoring
- **Prometheus & Grafana**: Performance monitoring

### AI Models
- **GPT-4.1**: Latest OpenAI model with enhanced capabilities
- **Claude 3.7 Sonnet**: Advanced context understanding
- **Gemini 2.0 Flash**: High performance with optimized cost
- **Grok 3**: Specialized technical translation features
- **Deepseek V3.1**: Optimized for Asian languages

## 🚀 Quick Start

### Prerequisites
- Node.js v18+
- MySQL 8.0+
- Redis 6.0+
- PM2 (for production)
- Git

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/ezai-translate.git
cd ezai-translate

# Install dependencies
npm install
cd client && npm install
```

2. **Environment Configuration**
```bash
# Copy example configuration
cp pm2/ecosystem.example.js pm2/ecosystem.config.js

# Edit the configuration file with your settings
nano pm2/ecosystem.config.js
```

3. **Database Setup**
```bash
# Create a new database in MySQL
# Run migrations
npx sequelize-cli db:migrate

# Seed initial data (optional)
npx sequelize-cli db:seed:all
```

4. **Start the Application**

**Development:**
```bash
# Backend
npm run dev:server

# Frontend (in a new terminal)
cd client
npm run dev
```

**Production:**
```bash
# Build frontend
cd client
npm run build

# Start all services
pm2 start pm2/ecosystem.config.js --env production
```

### Docker Setup (Alternative)

```bash
# Clone and navigate to project
git clone https://github.com/yourusername/ezai-translate.git
cd ezai-translate

# Start with Docker Compose
docker-compose up -d

# View logs
docker-compose logs -f
```

## 📁 Project Structure

```
ezai-translate/
├── client/                 # Next.js frontend
│   ├── src/
│   │   ├── app/           # App router pages
│   │   ├── components/    # Reusable components
│   │   ├── hooks/         # Custom hooks
│   │   ├── lib/           # Utility functions
│   │   └── types/         # TypeScript types
│   ├── public/            # Static assets
│   └── package.json
├── server/                # Backend API
│   ├── src/
│   │   ├── controllers/   # Route controllers
│   │   ├── models/        # Database models
│   │   ├── services/      # Business logic
│   │   ├── middleware/    # Express middleware
│   │   └── utils/         # Helper functions
│   ├── migrations/        # Database migrations
│   └── package.json
├── docs/                  # Documentation
├── pm2/                   # PM2 configuration
├── docker-compose.yml     # Docker setup
└── README.md
```

## 🔧 Configuration

### Environment Variables

Create a `.env` file in the root directory:

```env
# Database
DB_HOST=localhost
DB_PORT=3306
DB_NAME=ezai_translate
DB_USERNAME=your_username
DB_PASSWORD=your_password

# Redis
REDIS_HOST=localhost
REDIS_PORT=6379
REDIS_PASSWORD=your_redis_password

# API Keys
OPENAI_API_KEY=your_openai_key
ANTHROPIC_API_KEY=your_anthropic_key
GOOGLE_API_KEY=your_google_key

# Application
NODE_ENV=production
PORT=3000
JWT_SECRET=your_jwt_secret
CORS_ORIGIN=https://yourdomain.com
```

## 📖 API Documentation

### Authentication
```bash
# Get API token
POST /api/auth/login
{
  "email": "user@example.com",
  "password": "password"
}
```

### Translation Endpoints
```bash
# Text translation
POST /api/translate/text
{
  "text": "Hello world",
  "source_lang": "en",
  "target_lang": "vi",
  "domain": "general",
  "tone": "professional",
  "style": "straightforward"
}

# Document translation
POST /api/translate/document
# Multipart form data with file upload

# Get translation history
GET /api/translate/history?page=1&limit=10
```

### Usage Examples

```javascript
// Text Translation
const response = await fetch('/api/translate/text', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': `Bearer ${token}`
  },
  body: JSON.stringify({
    text: 'Hello world',
    source_lang: 'en',
    target_lang: 'vi',
    domain: 'general'
  })
});

const result = await response.json();
console.log(result.translation);
```

## 🧪 Testing

```bash
# Run all tests
npm run test

# Run tests with coverage
npm run test:coverage

# Run specific test suite
npm run test:unit
npm run test:integration
npm run test:e2e

# Frontend tests
cd client
npm run test
```

## 🚀 Deployment

### Using PM2 (Recommended)

```bash
# Production build
npm run build

# Start with PM2
pm2 start pm2/ecosystem.config.js --env production

# Monitor processes
pm2 monit

# View logs
pm2 logs
```

### Using Docker

```bash
# Build production image
docker build -t ezai-translate .

# Run container
docker run -p 3000:3000 -d ezai-translate

# Using docker-compose
docker-compose -f docker-compose.prod.yml up -d
```

### Environment-Specific Deployment

- **Development**: `npm run dev`
- **Staging**: `pm2 start ecosystem.config.js --env staging`
- **Production**: `pm2 start ecosystem.config.js --env production`

## 🔍 Monitoring & Maintenance

### Health Checks
```bash
# API health check
curl http://localhost:3000/api/health

# Database connection check
curl http://localhost:3000/api/health/db

# Redis connection check
curl http://localhost:3000/api/health/redis
```

### Performance Monitoring
- **Sentry**: Error tracking and performance monitoring
- **Prometheus**: Metrics collection
- **Grafana**: Visualization and alerting
- **PM2 Monitor**: Process monitoring

## 🤝 Contributing

We welcome contributions! Please read our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Style

- Use TypeScript for new code
- Follow ESLint and Prettier configurations
- Write tests for new features
- Update documentation as needed

## 📊 Statistics

- **100+** Supported Languages
- **1M+** Translations Completed
- **10+** Specialized Domains
- **95%** Translation Accuracy
- **99.9%** Uptime

## 🛣 Roadmap

- [ ] Mobile app development
- [ ] Real-time collaboration features
- [ ] Advanced OCR capabilities
- [ ] Voice translation
- [ ] API v2 with GraphQL
- [ ] Machine learning model fine-tuning
- [ ] Blockchain integration for translations

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- OpenAI for GPT models
- Anthropic for Claude models
- Google for Gemini models
- All contributors and beta testers

## 📞 Contact & Support

- **Website**: [https://ezaitranslate.com](https://ezaitranslate.com)
- **Email**: support@ezaitranslate.com
- **Documentation**: [https://docs.ezaitranslate.com](https://docs.ezaitranslate.com)
- **API Docs**: [https://api.ezaitranslate.com/docs](https://api.ezaitranslate.com/docs)

---

<div align="center">
  <p>Made with ❤️ by the EzAITranslate Team</p>
  <p>
    <a href="https://github.com/yourusername/ezai-translate/stargazers">⭐ Star us on GitHub</a> |
    <a href="https://twitter.com/ezaitranslate">🐦 Follow on Twitter</a> |
    <a href="https://linkedin.com/company/ezaitranslate">💼 LinkedIn</a>
  </p>
</div>
