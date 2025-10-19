# n8n Project Setup

This project contains an n8n workflow automation setup. n8n is a powerful workflow automation tool that allows you to connect different services and automate tasks.

## Prerequisites

Before setting up this project, ensure you have the following installed on your system:

- **Node.js** (version 16 or higher)
  - Download from [nodejs.org](https://nodejs.org/)
  - Verify installation: `node --version`
- **npm** (comes with Node.js)
  - Verify installation: `npm --version`
- **Git** (for cloning the repository)
  - Download from [git-scm.com](https://git-scm.com/)

## System Requirements

- **Operating System**: Windows, macOS, or Linux
- **Memory**: Minimum 2GB RAM (4GB+ recommended)
- **Storage**: At least 1GB free space
- **Network**: Internet connection for downloading dependencies

## Installation Instructions

### 1. Clone the Repository

```bash
git clone <repository-url>
cd n8n
```

### 2. Install Dependencies

Install all required Node.js packages:

```bash
npm install
```

This will install n8n and all its dependencies in the `node_modules` directory.

### 3. Environment Setup

Create a `.env` file in the project root for environment variables:

```bash
# Create .env file
touch .env
```

Add the following basic configuration to your `.env` file:

```env
# n8n Configuration
N8N_HOST=localhost
N8N_PORT=5678
N8N_PROTOCOL=http

# Database (optional - n8n uses SQLite by default)
# N8N_DATABASE_TYPE=sqlite
# N8N_DATABASE_SQLITE_DATABASE=n8n.db

# Security (recommended for production)
# N8N_USER_MANAGEMENT_JWT_SECRET=your-secret-key-here
# N8N_ENCRYPTION_KEY=your-encryption-key-here
```

### 4. Start n8n

Start the n8n application:

```bash
npm start
```

Or alternatively:

```bash
npx n8n start
```

### 5. Access n8n

Once started, n8n will be available at:
- **URL**: http://localhost:5678
- **Default credentials**: 
  - Email: `admin@example.com`
  - Password: `admin` (change this immediately!)

## First-Time Setup

### 1. Initial Login

1. Open your web browser
2. Navigate to `http://localhost:5678`
3. Create your first user account
4. Set up a secure password

### 2. Basic Configuration

1. Go to **Settings** → **Personal Settings**
2. Update your profile information
3. Configure your timezone and preferences

### 3. Security Setup

1. Go to **Settings** → **Users & Security**
2. Change the default admin password
3. Enable two-factor authentication (recommended)
4. Configure user management if needed

## Project Structure

```
n8n/
├── .gitignore          # Git ignore rules
├── .env               # Environment variables (create this)
├── package.json       # Project dependencies and scripts
├── package-lock.json  # Dependency lock file
├── node_modules/      # Installed packages (auto-generated)
├── README.md          # This file
└── .n8n/             # n8n data directory (auto-generated)
    ├── workflows/    # Workflow definitions
    ├── credentials/  # Stored credentials
    └── database.sqlite # Local database
```

## Available Scripts

- `npm start` - Start the n8n application
- `npm test` - Run tests (currently not configured)

## Configuration Options

### Environment Variables

Key environment variables you can configure:

```env
# Server Configuration
N8N_HOST=localhost          # Host to bind to
N8N_PORT=5678              # Port to listen on
N8N_PROTOCOL=http          # Protocol (http/https)

# Database Configuration
N8N_DATABASE_TYPE=sqlite   # Database type
N8N_DATABASE_SQLITE_DATABASE=n8n.db  # SQLite file path

# Security
N8N_USER_MANAGEMENT_JWT_SECRET=your-secret  # JWT secret
N8N_ENCRYPTION_KEY=your-encryption-key      # Encryption key

# Execution
N8N_EXECUTION_MODE=regular  # Execution mode
N8N_PAYLOAD_SIZE_MAX=16777216  # Max payload size

# Logging
N8N_LOG_LEVEL=info         # Log level (error, warn, info, debug)
```

### Advanced Configuration

For production deployments, consider:

1. **Database**: Use PostgreSQL or MySQL instead of SQLite
2. **Queue**: Configure Redis for better performance
3. **Webhooks**: Set up proper webhook URLs
4. **SSL**: Enable HTTPS with proper certificates

## Troubleshooting

### Common Issues

1. **Port already in use**
   ```bash
   # Change port in .env file
   N8N_PORT=5679
   ```

2. **Permission errors**
   ```bash
   # On Linux/macOS, you might need to run with sudo
   sudo npm start
   ```

3. **Database connection issues**
   ```bash
   # Reset database (WARNING: This will delete all data)
   rm .n8n/database.sqlite
   npm start
   ```

4. **Memory issues**
   ```bash
   # Increase Node.js memory limit
   node --max-old-space-size=4096 node_modules/n8n/bin/n8n start
   ```

### Logs

Check n8n logs for debugging:

```bash
# View logs
tail -f ~/.n8n/logs/n8n.log
```

## Development

### Adding Custom Nodes

1. Create a new directory for your custom nodes
2. Follow n8n's node development guidelines
3. Install your custom nodes in the project

### Workflow Development

1. Use the n8n web interface to create workflows
2. Export workflows as JSON files
3. Version control your workflow files

## Production Deployment

### Docker Deployment

```bash
# Using Docker
docker run -it --rm --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n
```

### PM2 Process Manager

```bash
# Install PM2
npm install -g pm2

# Start with PM2
pm2 start node_modules/n8n/bin/n8n --name "n8n" -- start
```

## Support and Resources

- **Official Documentation**: [docs.n8n.io](https://docs.n8n.io/)
- **Community Forum**: [community.n8n.io](https://community.n8n.io/)
- **GitHub Repository**: [github.com/n8n-io/n8n](https://github.com/n8n-io/n8n)
- **Discord Community**: [discord.gg/n8n](https://discord.gg/n8n)

## License

This project uses n8n, which is licensed under the [Sustainable Use License](https://github.com/n8n-io/n8n/blob/master/LICENSE.md).

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

---

**Note**: Remember to change the default admin credentials immediately after first setup for security purposes!
