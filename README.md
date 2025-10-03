# Auth0 Test - Node.js Express API

Modern Node.js and Express application setup with Auth0 integration support.

## 🚀 Tech Stack

- **Node.js** 18+ (LTS recommended, 24.5.0 latest)
- **Express** 5.1.0 (Latest stable)
- **pnpm** - Fast, disk space efficient package manager
- **Security**: Helmet, CORS
- **Development**: Nodemon, Morgan (logging)

## 📦 Prerequisites

- Node.js 18+ installed
- pnpm installed globally: `npm install -g pnpm`

## 🛠️ Setup Instructions

1. **Install dependencies**:
   ```bash
   pnpm install
   ```

2. **Configure environment variables**:
   - Copy `.env.example` to `.env`
   - Update the values with your Auth0 credentials

3. **Start development server**:
   ```bash
   pnpm dev
   ```

4. **Start production server**:
   ```bash
   pnpm start
   ```

## 📁 Project Structure

```
auth0-test/
├── node_modules/       # Dependencies
├── .env                # Environment variables (not in git)
├── .env.example        # Environment template
├── .gitignore          # Git ignore rules
├── .npmrc              # pnpm configuration
├── package.json        # Project dependencies
├── server.js           # Main application file
└── README.md           # This file
```

## 🔧 Available Scripts

- `pnpm start` - Start the production server
- `pnpm dev` - Start development server with auto-reload
- `pnpm lint` - Run ESLint (when configured)

## 🌐 API Endpoints

- `GET /` - Welcome message with API info
- `GET /health` - Health check endpoint

## 📝 Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `PORT` | Server port | 3000 |
| `NODE_ENV` | Environment mode | development |
| `ALLOWED_ORIGINS` | CORS allowed origins | * |
| `AUTH0_DOMAIN` | Auth0 domain | - |
| `AUTH0_CLIENT_ID` | Auth0 client ID | - |
| `AUTH0_CLIENT_SECRET` | Auth0 client secret | - |
| `AUTH0_CALLBACK_URL` | Auth0 callback URL | - |

## 🔐 Security Features

- **Helmet.js** - Sets secure HTTP headers
- **CORS** - Configurable cross-origin resource sharing
- **Environment Variables** - Sensitive data protection

## 🚀 Next Steps

1. Configure Auth0 credentials in `.env`
2. Add authentication routes
3. Implement protected endpoints
4. Add database integration (MongoDB, PostgreSQL, etc.)
5. Set up validation middleware with express-validator

## 📚 Documentation

- [Express 5.x Docs](https://expressjs.com/en/5x/api.html)
- [Auth0 Documentation](https://auth0.com/docs)
- [pnpm Documentation](https://pnpm.io/)

## 📄 License

ISC

