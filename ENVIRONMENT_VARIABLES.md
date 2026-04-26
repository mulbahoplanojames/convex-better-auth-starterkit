# Environment Variables - Next.js Implementation

This document lists all required and optional environment variables for the Convex Better Auth UI Next.js implementation.

## Required Environment Variables

### Convex Configuration
```bash
# Convex deployment URL (required)
NEXT_PUBLIC_CONVEX_URL=your-convex-deployment-url.convex.cloud

# Convex site URL (required)
NEXT_PUBLIC_CONVEX_SITE_URL=https://your-domain.com
# Alternative: CONVEX_SITE_URL=https://your-domain.com
```

### Email Configuration
```bash
# Email sender address (required for email features)
EMAIL_SEND_FROM=noreply@your-domain.com
```

## OAuth Provider Environment Variables

Configure these variables based on which OAuth providers you enable in `auth.constants.ts`.

### GitHub OAuth
```bash
GITHUB_CLIENT_ID=your-github-client-id
GITHUB_CLIENT_SECRET=your-github-client-secret
```

### Google OAuth
```bash
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-client-secret
```

### Facebook OAuth
```bash
FACEBOOK_CLIENT_ID=your-facebook-client-id
FACEBOOK_CLIENT_SECRET=your-facebook-client-secret
```

### Apple Sign In
```bash
APPLE_CLIENT_ID=your-apple-client-id
APPLE_CLIENT_SECRET=your-apple-client-secret
```

### Other OAuth Providers
```bash
# Atlassian
ATLASSIAN_CLIENT_ID=your-atlassian-client-id
ATLASSIAN_CLIENT_SECRET=your-atlassian-client-secret

# Discord
DISCORD_CLIENT_ID=your-discord-client-id
DISCORD_CLIENT_SECRET=your-discord-client-secret

# Figma
FIGMA_CLIENT_ID=your-figma-client-id
FIGMA_CLIENT_SECRET=your-figma-client-secret

# Line
LINE_CLIENT_ID=your-line-client-id
LINE_CLIENT_SECRET=your-line-client-secret

# Hugging Face
HUGGINGFACE_CLIENT_ID=your-huggingface-client-id
HUGGINGFACE_CLIENT_SECRET=your-huggingface-client-secret

# Kakao
KAKAO_CLIENT_ID=your-kakao-client-id
KAKAO_CLIENT_SECRET=your-kakao-client-secret

# Kick
KICK_CLIENT_ID=your-kick-client-id
KICK_CLIENT_SECRET=your-kick-client-secret

# PayPal
PAYPAL_CLIENT_ID=your-paypal-client-id
PAYPAL_CLIENT_SECRET=your-paypal-client-secret

# Salesforce
SALESFORCE_CLIENT_ID=your-salesforce-client-id
SALESFORCE_CLIENT_SECRET=your-salesforce-client-secret

# Slack
SLACK_CLIENT_ID=your-slack-client-id
SLACK_CLIENT_SECRET=your-slack-client-secret

# Notion
NOTION_CLIENT_ID=your-notion-client-id
NOTION_CLIENT_SECRET=your-notion-client-secret

# Naver
NAVER_CLIENT_ID=your-naver-client-id
NAVER_CLIENT_SECRET=your-naver-client-secret

# TikTok
TIKTOK_CLIENT_KEY=your-tiktok-client-key
TIKTOK_CLIENT_SECRET=your-tiktok-client-secret

# Twitch
TWITCH_CLIENT_ID=your-twitch-client-id
TWITCH_CLIENT_SECRET=your-twitch-client-secret

# Twitter/X
X_CLIENT_ID=your-x-client-id
X_CLIENT_SECRET=your-x-client-secret

# Dropbox
DROPBOX_CLIENT_ID=your-dropbox-client-id
DROPBOX_CLIENT_SECRET=your-dropbox-client-secret

# Linear
LINEAR_CLIENT_ID=your-linear-client-id
LINEAR_CLIENT_SECRET=your-linear-client-secret

# GitLab
GITLAB_CLIENT_ID=your-gitlab-client-id
GITLAB_CLIENT_SECRET=your-gitlab-client-secret

# Reddit
REDDIT_CLIENT_ID=your-reddit-client-id
REDDIT_CLIENT_SECRET=your-reddit-client-secret

# Roblox
ROBLOX_CLIENT_ID=your-roblox-client-id
ROBLOX_CLIENT_SECRET=your-roblox-client-secret

# Spotify
SPOTIFY_CLIENT_ID=your-spotify-client-id
SPOTIFY_CLIENT_SECRET=your-spotify-client-secret

# VK
VK_CLIENT_ID=your-vk-client-id
VK_CLIENT_SECRET=your-vk-client-secret

# Zoom
ZOOM_CLIENT_ID=your-zoom-client-id
ZOOM_CLIENT_SECRET=your-zoom-client-secret
```

## Optional Environment Variables

### Branding Customization
```bash
# Brand name for emails and UI (optional)
BRAND_NAME=Your App Name

# Brand tagline for emails (optional)
BRAND_TAGLINE=Your app tagline

# Brand logo URL for emails (optional)
BRAND_LOGO_URL=https://your-domain.com/logo.png
```

## Environment Setup

### Development (.env.local)
Create a `.env.local` file in the Next.js project root:

```bash
# Required Convex variables
NEXT_PUBLIC_CONVEX_URL=your-dev-convex-url.convex.cloud
NEXT_PUBLIC_CONVEX_SITE_URL=http://localhost:3000

# Email configuration
EMAIL_SEND_FROM=noreply@localhost

# OAuth providers (enable as needed)
GITHUB_CLIENT_ID=your-github-dev-client-id
GITHUB_CLIENT_SECRET=your-github-dev-client-secret
GOOGLE_CLIENT_ID=your-google-dev-client-id
GOOGLE_CLIENT_SECRET=your-google-dev-client-secret

# Branding (optional)
BRAND_NAME=Dev Auth
BRAND_TAGLINE=Development environment
```

### Production
Set these environment variables in your hosting platform (Vercel, Railway, etc.):

```bash
# Required Convex variables
NEXT_PUBLIC_CONVEX_URL=your-prod-convex-url.convex.cloud
NEXT_PUBLIC_CONVEX_SITE_URL=https://your-domain.com

# Email configuration
EMAIL_SEND_FROM=noreply@your-domain.com

# OAuth providers
GITHUB_CLIENT_ID=your-github-prod-client-id
GITHUB_CLIENT_SECRET=your-github-prod-client-secret
GOOGLE_CLIENT_ID=your-google-prod-client-id
GOOGLE_CLIENT_SECRET=your-google-prod-client-secret

# Branding
BRAND_NAME=Your App Name
BRAND_TAGLINE=Your app tagline
BRAND_LOGO_URL=https://your-domain.com/logo.png
```

## Provider Configuration

The enabled providers are controlled in `src/convex/auth.constants.ts`:

```typescript
export const AUTH_CONSTANTS: AuthConstants = {
    providers: {
        password: true,        // Email/password auth
        github: true,          // GitHub OAuth
        google: false,         // Google OAuth (set to true to enable)
        emailOTP: true,        // Email OTP verification
        magicLink: true,       // Magic link authentication
        // ... other providers
    },
    organizations: true,        // Organization management
    sendEmails: true,          // Email sending
    deviceAuthorization: true,  // Device authorization
    apiKeys: true,            // API key management
    brandName: 'self hosted Auth',
    brandTagline: 'Plug & Play Auth Widgets for your application.'
};
```

Only configure environment variables for providers that are enabled in this file.

## Convex Deployment Variables

When deploying to Convex, you'll also need:

```bash
# Convex deployment (automatically set by convex deploy)
CONVEX_DEPLOYMENT=your-deployment-id
```

## Email Service Configuration

The project uses Resend for email sending. Make sure to:

1. Install the Resend Convex integration: `@convex-dev/resend`
2. Configure your Resend API key in the Convex dashboard
3. Verify your sender domain in Resend

## Security Notes

- **Never commit `.env.local` to version control**
- **Use different client IDs/secrets for development and production**
- **Keep all secrets secure and rotate them regularly**
- **Use HTTPS in production for all OAuth callbacks**
- **Configure proper CORS settings in your OAuth provider dashboards**

## Troubleshooting

### Common Issues

1. **"NEXT_PUBLIC_CONVEX_URL must be set"**
   - Ensure the variable is set in `.env.local`
   - Restart your development server

2. **OAuth provider errors**
   - Verify client ID and secret are correct
   - Check callback URLs in provider dashboard
   - Ensure provider is enabled in `auth.constants.ts`

3. **Email not sending**
   - Verify `EMAIL_SEND_FROM` is set
   - Check Resend configuration and domain verification
   - Ensure `sendEmails` is `true` in auth constants

4. **Image optimization errors**
   - Ensure `NEXT_PUBLIC_CONVEX_URL` is set for image domains

### Variable Validation

The application will throw errors for missing required variables:
- `NEXT_PUBLIC_CONVEX_URL`
- `NEXT_PUBLIC_CONVEX_SITE_URL` or `CONVEX_SITE_URL`
- `EMAIL_SEND_FROM` (if email features are enabled)

OAuth provider variables are only validated when the provider is enabled in the configuration.
