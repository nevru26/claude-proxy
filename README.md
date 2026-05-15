# Claude API Proxy for Vercel

This is a simple serverless function that proxies requests to the Claude API to avoid CORS issues when calling from GitHub Pages.

## Files:
- `api/claude.js` - The serverless function
- `vercel.json` - Vercel configuration
- `package.json` - Project metadata

## Deploy to Vercel:

1. Create a new project in Vercel
2. Upload these 3 files
3. Deploy
4. You'll get a URL like: `https://your-project.vercel.app`
5. Your API endpoint will be: `https://your-project.vercel.app/api/claude`

## Usage from your app:

```javascript
const response = await fetch('https://your-project.vercel.app/api/claude', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    apiKey: 'your-claude-api-key',
    prompt: 'your prompt here'
  })
});

const data = await response.json();
```

## Security Note:
The API key is sent from the client but never stored on the server. It's only used to forward the request to Claude API.
