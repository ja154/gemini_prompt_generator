# Gemini Prompt Generator

A modern web application for generating AI responses using Google's Gemini API. Built with HTML, CSS (Tailwind), and vanilla JavaScript.

## Features

- **Real-time AI Generation**: Direct integration with Google's Gemini Pro API
- **Advanced Settings**: Configurable response length and creativity levels
- **Rate Limiting**: Built-in protection against API quota exceeded
- **Prompt History**: Local storage of recent prompts and responses
- **Responsive Design**: Mobile-first design with Tailwind CSS
- **Connection Testing**: Real-time API connection status monitoring
- **Usage Analytics**: Track API usage and rate limits

## Setup Instructions

### 1. Get Your Gemini API Key

1. Visit [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Sign in with your Google account
3. Click "Create API Key" button
4. Copy the generated API key

### 2. Configure the Application

1. Open the application in your browser
2. Navigate to **Settings** → **API Configuration Settings**
3. Paste your API key in the "API Key" field
4. Click "Save API Key"
5. Test the connection using the "Test Connection" button

### 3. Development Setup

```bash
# Install dependencies
npm install

# Build CSS (one-time)
npm run build:css

# Watch for changes during development
npm run watch:css

# Start development server
npm run dev
```

## Project Structure

```
├── css/
│   ├── main.css              # Generated Tailwind CSS (don't edit)
│   └── tailwind.css          # Source Tailwind CSS with custom styles
├── pages/
│   ├── ai_prompt_interface.html     # Main AI interface
│   ├── api_configuration_settings.html  # Settings page
│   ├── response_history_dashboard.html  # History page
│   └── system_status_monitor.html   # Status monitoring
├── public/
│   ├── gemini-api.js         # Gemini API client and utilities
│   ├── favicon.ico
│   └── manifest.json
├── index.html                # Landing page with loading animation
├── package.json              # Dependencies and scripts
└── tailwind.config.js        # Tailwind configuration
```

## API Integration

### Gemini API Client (`public/gemini-api.js`)

The application includes a comprehensive API client with:

- **Rate Limiting**: Automatic enforcement of API limits (10/minute, 500/hour)
- **Error Handling**: Graceful error management and user feedback
- **Connection Testing**: Real-time API connectivity validation
- **Usage Tracking**: Monitor API consumption and limits

### Key Features

```javascript
// Generate content with custom options
const result = await geminiAPI.generateContent(prompt, {
    responseLength: 'medium',    // short, medium, long
    creativityLevel: 'balanced', // conservative, balanced, creative
    userId: 'user123'
});

// Test API connection
const connectionTest = await geminiAPI.testConnection();

// Get usage statistics
const stats = geminiAPI.getUserStats();
```

## Security Features

- **Client-side API Key Storage**: Keys stored locally in browser
- **Rate Limiting Protection**: Prevents API quota violations
- **Input Validation**: Sanitized user inputs
- **Error Boundary**: Graceful error handling

## Usage Guidelines

### Response Length Options
- **Short**: 1-2 paragraphs (≤500 tokens)
- **Medium**: 3-5 paragraphs (≤1000 tokens)
- **Long**: 6+ paragraphs (≤2000 tokens)

### Creativity Levels
- **Conservative**: Temperature 0.2 - Focused, factual responses
- **Balanced**: Temperature 0.7 - Natural, versatile responses
- **Creative**: Temperature 0.9 - Imaginative, diverse responses

## Rate Limits

The application enforces the following limits:
- **10 requests per minute** per user
- **500 requests per hour** per user

Rate limit status is displayed in real-time on the interface.

## Browser Compatibility

- Chrome 88+
- Firefox 85+
- Safari 14+
- Edge 88+

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

MIT License - see LICENSE file for details

## Support

For issues or questions:
1. Check the connection status in Settings
2. Verify your API key is valid
3. Check browser console for errors
4. Review rate limit status

## Environment Variables

Create a `.env` file in the root directory:

```env
# Gemini API Configuration
GEMINI_API_KEY=your_gemini_api_key
```

**Note**: For client-side applications, the API key is stored in localStorage. For production deployments, consider using a backend proxy to protect your API key.