# LABTANAM Backend - Vercel Deployment Guide

## Prerequisites

1. Vercel account (free tier available)
2. GitHub account with your code repository
3. Environment variables ready

## Deployment Steps

### 1. Connect Repository to Vercel

1. Visit [vercel.com](https://vercel.com) and sign in
2. Click "New Project"
3. Import your GitHub repository containing the backend
4. Select the `backend` folder as the root directory

### 2. Configure Environment Variables

In Vercel dashboard, go to your project settings and add these environment variables:

```
NODE_ENV=production
SUPABASE_URL=your_supabase_url_here
SUPABASE_ANON_KEY=your_supabase_anon_key_here
OPENAI_API_KEY=your_openai_api_key_here
GEMINI_API_KEY=your_gemini_api_key_here
```

### 3. Deploy

Vercel will automatically deploy your backend. The API will be available at:
- `https://your-project-name.vercel.app/api/chat`
- `https://your-project-name.vercel.app/api/logbook`
- `https://your-project-name.vercel.app/api/health`

### 4. Update Frontend

Update the frontend JavaScript files to use your Vercel backend URL:

In `frontend/js/chatbot.js`:
```javascript
this.apiEndpoint = 'https://your-project-name.vercel.app/api/chat';
```

In `frontend/js/logbook.js`:
```javascript
this.apiEndpoint = 'https://your-project-name.vercel.app/api/logbook';
```

## Project Structure

```
backend/
├── api/
│   ├── chat/
│   │   └── index.js      # Chat API endpoint
│   ├── logbook/
│   │   └── index.js      # Logbook API endpoint
│   ├── health.js         # Health check endpoint
│   └── index.js          # Root API endpoint
├── routes/
│   ├── chat.js           # Chat route handlers
│   └── logbook.js        # Logbook route handlers
├── server.js             # Main server (for local development)
├── package.json
├── vercel.json           # Vercel configuration
└── .env.example          # Environment variables template
```

## Features

- ✅ Serverless deployment on Vercel
- ✅ Automatic HTTPS
- ✅ CORS configuration for frontend
- ✅ Rate limiting
- ✅ Health checks
- ✅ Environment-based configuration

## Testing

Once deployed, test your endpoints:

1. Health check: `GET https://your-project-name.vercel.app/api/health`
2. Chat API: `POST https://your-project-name.vercel.app/api/chat`
3. Logbook API: `GET/POST https://your-project-name.vercel.app/api/logbook`

## Troubleshooting

- Check Vercel logs in the dashboard for errors
- Ensure all environment variables are set
- Verify CORS origins match your frontend domain
- Check rate limiting if getting 429 errors