# Daksh Inventory

**A comprehensive inventory management and audit system**

> An intelligent inventory tracking solution designed for efficient management, real-time audits, and detailed reporting.

![Status](https://img.shields.io/badge/status-active-success)
![License](https://img.shields.io/badge/license-MIT-blue)

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

- **Real-time Inventory Tracking** - Monitor stock levels instantly
- **Audit Trails** - Complete history of all inventory transactions
- **Smart Analytics** - Insights and reports on inventory patterns
- **User Management** - Role-based access control
- **Multi-location Support** - Manage inventory across multiple warehouses
- **Automated Alerts** - Low stock and threshold notifications
- **REST API** - Full-featured API for integrations
- **Responsive Design** - Works on desktop, tablet, and mobile

## 🛠️ Tech Stack

### Backend
- **Runtime**: Node.js (v18+)
- **Framework**: Express.js
- **Database**: MongoDB / PostgreSQL
- **Authentication**: JWT
- **Testing**: Jest

### Frontend
- **Framework**: React / Vue.js
- **Styling**: Tailwind CSS
- **State Management**: Redux / Pinia
- **Build Tool**: Vite

### DevOps
- **Containerization**: Docker
- **Version Control**: Git
- **CI/CD**: GitHub Actions
- **Deployment**: AWS / Heroku / Render

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18 or higher) - [Download](https://nodejs.org/)
- **npm** or **yarn** (v9+)
- **Git** - [Download](https://git-scm.com/)
- **Docker** (optional, for containerized deployment)
- **Database**: MongoDB or PostgreSQL

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/amitsvision4u-glitch/daksh-inventory.git
cd daksh-inventory
```

### 2. Install Dependencies

```bash
# Install backend dependencies
npm install

# If using monorepo with separate frontend
cd frontend && npm install && cd ..
```

### 3. Setup Environment Variables

```bash
# Copy the example environment file
cp .env.example .env

# Edit .env with your configuration
nano .env
```

### 4. Initialize Database

```bash
# Run database migrations/seeds (if applicable)
npm run db:setup
```

## ⚙️ Configuration

### Environment Variables

Create a `.env` file in the root directory:

```env
# Server
NODE_ENV=development
PORT=5000
API_URL=http://localhost:5000

# Database
DB_HOST=localhost
DB_PORT=27017
DB_NAME=daksh_inventory
DB_USER=admin
DB_PASSWORD=your_password

# Authentication
JWT_SECRET=your_jwt_secret_key
JWT_EXPIRE=7d

# Frontend
REACT_APP_API_URL=http://localhost:5000/api
VITE_API_URL=http://localhost:5000/api
```

See `.env.example` for all available options.

## 💻 Usage

### Development Mode

```bash
# Start the development server
npm run dev

# Start with hot reload (frontend)
cd frontend && npm run dev

# Start backend and frontend concurrently
npm run dev:all
```

The application will be available at:
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000

### Production Build

```bash
# Build the frontend
npm run build

# Build the backend
npm run build:server

# Start production server
npm start
```

## 📁 Project Structure

```
daksh-inventory/
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── middleware/
│   │   ├── utils/
│   │   └── index.js
│   ├── tests/
│   ├── .env.example
│   ├── package.json
│   └── server.js
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── store/
│   │   ├── services/
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── public/
│   ├── package.json
│   └── vite.config.js
├── docker-compose.yml
├── Dockerfile
├── .gitignore
├── .env.example
├── package.json
└── README.md
```

## 🔌 API Documentation

### Base URL
```
http://localhost:5000/api/v1
```

### Example Endpoints

**Get all inventory items**
```bash
GET /api/v1/inventory
Authorization: Bearer <token>
```

**Create new item**
```bash
POST /api/v1/inventory
Content-Type: application/json
Authorization: Bearer <token>

{
  "name": "Product Name",
  "sku": "SKU123",
  "quantity": 100,
  "price": 29.99
}
```

**Get audit logs**
```bash
GET /api/v1/audit/logs
Authorization: Bearer <token>
```

For complete API documentation, see [API.md](./API.md) or visit `/api-docs` after starting the server.

## 🌐 Deployment

### Deploy to Heroku

```bash
# Login to Heroku
heroku login

# Create a new app
heroku create daksh-inventory

# Set environment variables
heroku config:set NODE_ENV=production -a daksh-inventory

# Deploy
git push heroku main
```

### Deploy to Render

1. Connect your GitHub repository to [Render](https://render.com)
2. Create a new Web Service
3. Set build command: `npm install`
4. Set start command: `npm start`
5. Add environment variables
6. Deploy

### Deploy with Docker

```bash
# Build the image
docker build -t daksh-inventory .

# Run container
docker run -p 5000:5000 --env-file .env daksh-inventory

# Or use docker-compose
docker-compose up -d
```

### Deploy to AWS

- Use **AWS Elastic Beanstalk** for easy deployment
- Use **AWS RDS** for managed database
- Use **CloudFront** for CDN

## 📝 Contributing

We welcome contributions! Here's how you can help:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please ensure:
- Code follows the existing style
- Tests are included and passing
- README is updated if needed
- Commit messages are clear and descriptive

## 🧪 Testing

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:coverage

# Run tests in watch mode
npm run test:watch
```

## 🐛 Troubleshooting

### Port Already in Use
```bash
# Find process using port 5000
lsof -i :5000

# Kill the process
kill -9 <PID>
```

### Database Connection Issues
- Verify MongoDB/PostgreSQL is running
- Check connection string in `.env`
- Ensure credentials are correct

### Build Failures
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

## 📊 Monitoring & Logging

- Application logs are stored in `logs/` directory
- Use `npm run logs` to view real-time logs
- Integration with services like Datadog, LogRocket available

## 🔐 Security

- All API endpoints require authentication
- Passwords are hashed with bcrypt
- SQL injection protection via parameterized queries
- CORS enabled with whitelist configuration
- Rate limiting implemented
- Environment variables for sensitive data

## 📄 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## 👥 Support & Contact

- **Issues**: [GitHub Issues](https://github.com/amitsvision4u-glitch/daksh-inventory/issues)
- **Discussions**: [GitHub Discussions](https://github.com/amitsvision4u-glitch/daksh-inventory/discussions)
- **Email**: support@daksh-inventory.dev

## 📚 Additional Resources

- [Express.js Documentation](https://expressjs.com/)
- [React Documentation](https://react.dev/)
- [MongoDB Manual](https://docs.mongodb.com/manual/)
- [JWT Introduction](https://jwt.io/introduction)

---

**Made with ❤️ by Amit**

*Last updated: 2026-04-23*
