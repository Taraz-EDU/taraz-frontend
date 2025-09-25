# Deployment Guide

This project is configured to automatically deploy to Fly.io using GitHub Actions.

## Setup

### 1. Fly.io Setup

1. Install the Fly.io CLI: https://fly.io/docs/hands-on/install-flyctl/
2. Login to Fly.io: `flyctl auth login`
3. Create your app: `flyctl apps create taraz-frontend`
4. Get your API token: `flyctl auth token`

### 2. GitHub Secrets

Add the following secrets to your GitHub repository:

- `FLY_API_TOKEN`: Your Fly.io API token (get it with `flyctl auth token`)

### 3. Environment Variables

If you need environment variables for production, add them to your Fly.io app:

```bash
flyctl secrets set KEY=value --app taraz-frontend
```

## Deployment Workflows

### Production Deployment
- **Trigger**: Push to `main` branch
- **Workflow**: `.github/workflows/deploy.yml`
- **App**: `taraz-frontend`

### Staging Deployment
- **Trigger**: Push to `develop` or `staging` branches
- **Workflow**: `.github/workflows/deploy-staging.yml`
- **App**: `taraz-frontend`

## Manual Deployment

You can also deploy manually:

```bash
# Deploy to production
flyctl deploy --app taraz-frontend

# Deploy with remote build
flyctl deploy --remote-only --app taraz-frontend
```

## Monitoring

Check your app status:

```bash
flyctl status --app taraz-frontend
flyctl logs --app taraz-frontend
```

## Configuration

The app configuration is in `fly.toml`:
- **Region**: Frankfurt (fra)
- **Memory**: 1GB
- **CPU**: 1 shared CPU
- **Port**: 3000
- **Auto-scaling**: Enabled (stops when idle, starts on demand)
