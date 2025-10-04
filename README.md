# Auth0 Express Authentication Project

A modern Node.js Express application with Auth0 integration for secure user authentication and authorization.

## 🚀 Features

- **Express.js 5.x** - Modern Node.js web framework
- **Auth0 Integration** - Secure authentication and authorization
- **OpenID Connect** - Industry-standard authentication protocol
- **Protected Routes** - Secure endpoints with automatic login redirects
- **Environment Configuration** - Secure credential management
- **Security Middleware** - Helmet, CORS, and other security best practices
- **Development Tools** - Nodemon for hot reloading

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18.0.0 or higher)
- **pnpm** (v8.0.0 or higher) - Package manager
- **Auth0 Account** - For authentication services

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd auth0-test
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Then edit `.env` with your Auth0 credentials:
   ```env
   AUTH0_SECRET=your-secret-here
   AUTH0_BASE_URL=http://localhost:3000
   AUTH0_CLIENT_ID=your-client-id
   AUTH0_ISSUER_BASE_URL=https://your-domain.auth0.com
   ```

## 🔧 Auth0 Configuration

### 1. Create an Auth0 Application

1. Log in to your [Auth0 Dashboard](https://manage.auth0.com)
2. Navigate to **Applications** → **Applications**
3. Click **Create Application**
4. Choose **Regular Web Application**
5. Click **Create**

### 2. Configure Application Settings

In your Auth0 application settings, configure the following URLs:

**Allowed Callback URLs:**
```
http://localhost:3000/callback
```

**Allowed Logout URLs:**
```
http://localhost:3000
```

**Allowed Web Origins:**
```
http://localhost:3000
```

### 3. Get Your Credentials

From your Auth0 application settings, copy:
- **Client ID** → `AUTH0_CLIENT_ID`
- **Domain** → `AUTH0_ISSUER_BASE_URL` (format: `https://your-domain.auth0.com`)

## 🚀 Running the Application

### Development Mode
```bash
pnpm dev
```

### Production Mode
```bash
pnpm start
```

The server will start on `http://localhost:3000`

## 🧪 Testing the Application

### 1. Basic Server Test
Visit `http://localhost:3000` to see the API status:
```json
{
  "message": "Welcome to Express API with Auth0",
  "version": "1.0.0",
  "timestamp": "2025-01-03T23:55:57.309Z",
  "authenticated": false,
  "user": null
}
```

### 2. Authentication Flow Test

#### Step 1: Access Protected Route
Visit `http://localhost:3000/profile`
- You should be **automatically redirected** to Auth0 login page
- This demonstrates the `requiresAuth()` middleware working

#### Step 2: Login Process
1. On the Auth0 login page, enter your credentials
2. After successful login, you'll be redirected back to `/profile`
3. You should see your user profile data:
   ```json
   {
     "message": "Protected profile data",
     "user": {
       "sub": "auth0|user-id",
       "name": "Your Name",
       "email": "your@email.com",
       "email_verified": true,
       "picture": "https://...",
       "updated_at": "2025-01-03T23:55:57.309Z"
     }
   }
   ```

#### Step 3: Verify Authentication Status
Visit `http://localhost:3000/` again:
- `"authenticated": true` should now show
- `"user"` should contain your profile data

#### Step 4: Test Logout
Visit `http://localhost:3000/logout`
- You'll be logged out and redirected to the home page
- Visit `/profile` again to confirm you're redirected to login

### 3. API Endpoints Testing

Use curl or your preferred HTTP client:

#### Health Check
```bash
curl http://localhost:3000/health
```

#### Home (Public)
```bash
curl http://localhost:3000/
```

#### Profile (Protected - requires authentication)
```bash
curl http://localhost:3000/profile
# Should redirect to Auth0 login if not authenticated
```

## 📚 API Endpoints

| Method | Endpoint | Description | Authentication |
|--------|----------|-------------|----------------|
| `GET` | `/` | API status and auth state | None |
| `GET` | `/health` | Server health check | None |
| `GET` | `/profile` | User profile data | Required |
| `GET` | `/login` | Auth0 login page | None |
| `GET` | `/logout` | Auth0 logout | None |
| `GET` | `/callback` | Auth0 callback handler | None |

## 🔒 Security Features

- **Helmet.js** - Security headers
- **CORS** - Cross-origin resource sharing configuration
- **Environment Variables** - Sensitive data protection
- **Auth0 Integration** - Industry-standard authentication
- **Protected Routes** - Automatic authentication enforcement

## 🛠️ Development

### Project Structure
```
auth0-test/
├── server.js          # Main application file
├── package.json       # Dependencies and scripts
├── .env              # Environment variables (not in git)
├── .env.example      # Environment template
├── .gitignore        # Git ignore rules
└── README.md         # This file
```

### Available Scripts

- `pnpm start` - Start the production server
- `pnpm dev` - Start development server with nodemon
- `pnpm lint` - Run ESLint

### Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `AUTH0_SECRET` | Long random string for session encryption | `b6ac1c75c1e00edf...` |
| `AUTH0_BASE_URL` | Your application's base URL | `http://localhost:3000` |
| `AUTH0_CLIENT_ID` | Your Auth0 application client ID | `1CTz27yPHBvBAZB...` |
| `AUTH0_ISSUER_BASE_URL` | Your Auth0 domain | `https://dev-npb1db6k...` |
| `PORT` | Server port | `3000` |
| `NODE_ENV` | Environment | `development` |

## 🐛 Troubleshooting

### Common Issues

#### 1. "Invalid callback URL" Error
- Check your Auth0 application settings
- Ensure `http://localhost:3000/callback` is in **Allowed Callback URLs**

#### 2. "Invalid logout URL" Error
- Add `http://localhost:3000` to **Allowed Logout URLs** in Auth0

#### 3. "Invalid client" Error
- Verify your `AUTH0_CLIENT_ID` matches your Auth0 application
- Check that `AUTH0_ISSUER_BASE_URL` is correct

#### 4. Session/Secret Issues
- Generate a new secret: `node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"`
- Update your `.env` file with the new secret

#### 5. CORS Issues
- Ensure `AUTH0_BASE_URL` matches your actual application URL
- Check CORS settings in your Auth0 application

### Debug Mode
Set `NODE_ENV=development` in your `.env` file for detailed error messages.

## 📖 Auth0 Documentation

- [Auth0 Express Quickstart](https://auth0.com/docs/quickstart/webapp/express)
- [Express OpenID Connect](https://github.com/auth0/express-openid-connect)
- [Auth0 Dashboard](https://manage.auth0.com)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the ISC License.

## 🆘 Support

If you encounter any issues:

1. Check the [troubleshooting section](#-troubleshooting)
2. Review the [Auth0 documentation](#-auth0-documentation)
3. Create an issue in the repository

---

**Happy coding! 🎉**