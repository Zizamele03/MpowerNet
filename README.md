# Jobs & Economic Resilience

A mobile-first, production-ready application to help job seekers, entrepreneurs, and small businesses with AI-driven video interview practice, tender & funding discovery, funding applications, and localized entrepreneurship ideas.

## Features

### For Job Seekers
- **Job Discovery**: Advanced search and filtering for job opportunities
- **AI-Powered Interview Practice**: Record video responses and get AI feedback
- **Application Tracking**: Manage job applications and track status
- **Skill Development**: Personalized learning recommendations

### For Businesses
- **Job Posting**: Create and manage job listings
- **Candidate Management**: Review applications and manage hiring pipeline
- **Tender Discovery**: Find and subscribe to relevant tenders
- **Funding Opportunities**: Access funding and grant opportunities

### For Entrepreneurs
- **AI-Generated Business Ideas**: Get personalized entrepreneurship ideas
- **Tender Subscriptions**: Stay updated on relevant tenders
- **Funding Applications**: Create and manage funding applications
- **Proposal Generation**: AI-assisted proposal writing

## 🛠 Technology Stack

### Frontend
- **Flutter** - Cross-platform mobile and web development
- **Riverpod** - State management
- **Material 3** - Modern UI design system
- **GoRouter** - Navigation and routing

### Backend
- **Node.js** - JavaScript runtime
- **TypeScript** - Type-safe JavaScript
- **Express.js** - Web framework
- **MongoDB** - NoSQL database
- **Redis** - Caching and job queue
- **JWT** - Authentication

### AI & ML
- **OpenAI API** - AI-powered features
- **Mock AI Service** - Development fallback
- **Video Analysis** - Interview feedback
- **Content Generation** - Business ideas and proposals

### Infrastructure
- **Google Cloud Platform** - Cloud hosting
- **Cloud Run** - Serverless containers
- **Terraform** - Infrastructure as Code
- **GitHub Actions** - CI/CD pipeline
- **Docker** - Containerization

## 🏗 Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Flutter App   │    │   Web Client    │    │   Admin Panel   │
│   (Mobile)      │    │   (Desktop)     │    │   (Web)         │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────┐
                    │   API Gateway    │
                    │   (Cloud Run)   │
                    └─────────────────┘
                                 │
                    ┌─────────────────┐
                    │   Backend API   │
                    │   (Node.js)     │
                    └─────────────────┘
                                 │
         ┌───────────────────────┼───────────────────────┐
         │                       │                       │
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   MongoDB       │    │   Redis Queue   │    │   AI Service    │
│   (Database)    │    │   (Background)  │    │   (OpenAI)      │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## Quick Start

### Prerequisites
- Docker and Docker Compose
- Node.js 18+ (for development)
- Flutter 3.0+ (for frontend development)

### Option 1: Docker Setup (Recommended)

```bash
# Clone the repository
git clone <REPO_URL>
cd jobs-economic-resilience

# Start all services
docker-compose up -d

# Seed the database
docker-compose exec api npm run seed

# Access the application
# API: http://localhost:3000
# API Docs: http://localhost:3000/api-docs
```

### Option 2: Local Development

```bash
# Backend setup
cd backend
npm install
cp env.example .env
npm run dev

# Frontend setup (in new terminal)
cd frontend
flutter pub get
flutter run -d chrome

# Start database services
docker run -d --name mongodb -p 27017:27017 mongo:7.0
docker run -d --name redis -p 6379:6379 redis:7.2-alpine
```

## Demo Accounts

The seed script creates three demo accounts:

| Role | Email | Password | Features |
|------|-------|----------|----------|
| Jobseeker | jobseeker@example.com | password123 | Browse jobs, apply, practice interviews |
| Business | business@example.com | password123 | Post jobs, manage applications |
| Admin | admin@example.com | password123 | User management, system administration |

## Core Features

### 1. Job Management
- **Search & Filter**: Advanced job search with multiple filters
- **Application Tracking**: Manage job applications and status
- **Company Profiles**: Detailed company information
- **Recommendations**: Personalized job suggestions

### 2. Interview Practice
- **AI Question Generation**: Context-aware interview questions
- **Video Recording**: In-app video recording capabilities
- **AI Feedback**: Comprehensive performance analysis
- **Progress Tracking**: Monitor improvement over time

### 3. Tender & Funding
- **Tender Discovery**: Browse and subscribe to tenders
- **Funding Applications**: Create and manage funding requests
- **AI Proposal Generation**: AI-assisted proposal writing
- **Document Management**: Secure document storage and sharing

### 4. AI-Powered Features
- **Smart Recommendations**: Personalized content suggestions
- **Content Generation**: AI-generated business ideas and proposals
- **Video Analysis**: Advanced interview performance analysis
- **Natural Language Processing**: Intelligent content understanding

## Development

### Backend Development

```bash
cd backend

# Install dependencies
npm install

# Run in development mode
npm run dev

# Run tests
npm test

# Run linting
npm run lint

# Build for production
npm run build
```

### Frontend Development

```bash
cd frontend

# Install dependencies
flutter pub get

# Generate code
flutter packages pub run build_runner build

# Run on web
flutter run -d chrome

# Run on mobile
flutter run

# Run tests
flutter test
```

### API Documentation

- **Swagger UI**: http://localhost:3000/api-docs
- **OpenAPI Spec**: Available in `/docs` folder
- **Postman Collection**: Available in `/docs/postman/`

## Deployment

### Production Deployment

1. **Set up GCP Project**
   ```bash
   gcloud projects create <PROJECT_ID>
   gcloud config set project <PROJECT_ID>
   ```

2. **Deploy Infrastructure**
   ```bash
   cd infra/terraform
   terraform init
   terraform plan
   terraform apply
   ```

3. **Configure Secrets**
   ```bash
   gcloud secrets create mongodb-uri --data-file=- <<< "your-mongodb-uri"
   gcloud secrets create jwt-secret --data-file=- <<< "your-jwt-secret"
   ```

4. **Deploy Application**
   ```bash
   git push origin main  # Triggers CI/CD pipeline
   ```

### Local Production Testing

```bash
# Build and run with production settings
docker-compose -f docker-compose.prod.yml up -d
```

## Monitoring & Analytics

### Health Checks
- **API Health**: `GET /health`
- **Database**: Connection status monitoring
- **External Services**: OpenAI API availability

### Metrics
- **Performance**: Response times and throughput
- **Usage**: User engagement and feature adoption
- **Errors**: Error rates and types
- **Security**: Authentication and authorization events

### Logging
- **Structured Logging**: JSON-formatted logs
- **Log Levels**: Debug, Info, Warn, Error
- **Log Aggregation**: Centralized log collection
- **Alerting**: Automated alerting for critical events

## Security

### Authentication & Authorization
- **JWT Tokens**: Secure token-based authentication
- **Role-Based Access**: Granular permission system
- **Password Security**: bcrypt hashing with salt
- **Session Management**: Secure session handling

### Data Protection
- **Encryption**: Data encryption at rest and in transit
- **PII Handling**: Privacy-compliant data processing
- **Video Security**: Secure video storage and processing
- **Input Validation**: Comprehensive input sanitization

### Compliance
- **GDPR**: European data protection compliance
- **Privacy by Design**: Built-in privacy protections
- **Data Retention**: Automated data lifecycle management
- **Audit Logging**: Comprehensive audit trails

## Testing

### Backend Testing
```bash
# Unit tests
npm run test

# Integration tests
npm run test:integration

# Coverage report
npm run test:coverage
```

### Frontend Testing
```bash
# Unit tests
flutter test

# Widget tests
flutter test test/widget_test.dart

# Integration tests
flutter test integration_test/
```

### API Testing
```bash
# Health check
curl http://localhost:3000/health

# Authentication
curl -X POST http://localhost:3000/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"jobseeker@example.com","password":"password123"}'
```

## Documentation

- **[Architecture](docs/ARCHITECTURE.md)**: System architecture and design
- **[Deployment](docs/DEPLOYMENT.md)**: Deployment and infrastructure guide
- **[Security](docs/SECURITY.md)**: Security measures and compliance
- **[Demo](docs/DEMO.md)**: Demo scenarios and testing guide
- **[API Documentation](docs/API.md)**: Complete API reference
- **[OpenAI Prompts](docs/OPENAI_PROMPTS.md)**: AI prompt documentation

## Contributing

### Development Workflow
1. **Fork** the repository
2. **Create** a feature branch
3. **Make** your changes
4. **Add** tests for new features
5. **Run** the test suite
6. **Submit** a pull request

### Code Standards
- **TypeScript**: Strict type checking enabled
- **ESLint**: Code linting and formatting
- **Prettier**: Code formatting
- **Conventional Commits**: Standardized commit messages

### Pull Request Process
1. **Description**: Clear description of changes
2. **Testing**: Include test results
3. **Documentation**: Update relevant documentation
4. **Review**: Address reviewer feedback

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

### Getting Help
- **Documentation**: Check the `/docs` folder
- **Issues**: Create GitHub issues for bugs
- **Discussions**: Use GitHub discussions for questions
- **Email**: support@jobs-economic-resilience.com

### Community
- **Discord**: Join our community server
- **GitHub**: Star and watch the repository
- **Twitter**: Follow for updates
- **LinkedIn**: Connect with the team

## 🗺 Roadmap

### Phase 1 (Current)
-  Core job management
-  Interview practice
-  Basic AI integration
-  User authentication

### Phase 2 (Next)
-  Real-time notifications
-  Advanced AI features
-  Mobile app stores
-  Analytics dashboard

### Phase 3 (Future)
-  Microservices architecture
-  Event-driven design
-  Machine learning integration
-  Real-time collaboration

##  Acknowledgments

- **OpenAI** for AI capabilities
- **Google Cloud** for infrastructure
- **Flutter** for cross-platform development
- **MongoDB** for database services
- **Open Source Community** for amazing tools

---

**Built with love for job seekers, entrepreneurs, and small businesses worldwide.**


