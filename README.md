<div align="center">

# Tweetly

### AI-Powered Tweet Generator for Makers, Developers & Creators

Transform your daily progress into polished, engaging tweets with the power of AI.

[![Live Demo](https://img.shields.io/badge/Live_Demo-usetweetly.vercel.app-0A66C2?style=for-the-badge&logo=vercel&logoColor=white)](https://usetweetly.vercel.app)

**React 19** · **TypeScript** · **Express 5** · **Supabase** · **Llama 3 70B**

</div>

---

## The Problem

Building in public is powerful, but crafting the perfect tweet for every update is time-consuming. Developers and makers often struggle to:

- Convert technical progress into engaging social content
- Maintain a consistent posting tone
- Balance between informative and entertaining

**Tweetly solves this** by using AI to transform your raw progress updates into tweet-ready content that matches your style and voice.

---

## Features

### Core Capabilities

| Feature | Description |
|---------|-------------|
| **AI-Powered Generation** | Leverages Llama 3 70B via OpenRouter to craft intelligent, context-aware tweets |
| **Customizable Tone** | Choose from **Funny**, **Professional**, **Motivational**, or **Sarcastic** styles |
| **Flexible Length** | Generate **Short** tweets, **Medium** posts, full **Threads**, or **Twitter-Free** content |
| **Tweet History** | All generated tweets are securely saved to your account for future reference |
| **Google OAuth** | Seamless authentication powered by Supabase |
| **Modern UI** | Sleek dark theme with smooth Framer Motion animations |

### How It Works

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Your Input    │────▶│   AI Engine     │────▶│  Perfect Tweet  │
│                 │     │                 │     │                 │
│ "Fixed auth bug │     │ Analyzes tone,  │     │ "Just squashed  │
│  that took 3    │     │ applies style,  │     │  an auth bug    │
│  hours to find" │     │ generates tweet │     │  that played    │
│                 │     │                 │     │  hide & seek    │
│                 │     │                 │     │  for 3 hours!"  │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

> **Note**: Tweetly generates tweets for you to copy and share. Direct posting to Twitter/X is not available due to API limitations.

---

## Tech Stack

<table>
<tr>
<td align="center" width="50%">

### Frontend

![React](https://img.shields.io/badge/React_19-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat-square&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/Vite_7-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![Framer Motion](https://img.shields.io/badge/Framer_Motion-0055FF?style=flat-square&logo=framer&logoColor=white)

- **React 19** with TypeScript
- **Vite 7** for lightning-fast builds
- **Tailwind CSS** for utility-first styling
- **Framer Motion** for fluid animations
- **React Router** for SPA navigation

</td>
<td align="center" width="50%">

### Backend

![Node.js](https://img.shields.io/badge/Node.js-43853D?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express_5-000000?style=flat-square&logo=express&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-181818?style=flat-square&logo=supabase&logoColor=3FCF8E)
![OpenRouter](https://img.shields.io/badge/OpenRouter-FF6B6B?style=flat-square&logo=openai&logoColor=white)

- **Express 5** REST API
- **Supabase** for auth & database
- **OpenRouter** AI integration
- **Llama 3 70B** language model
- **TypeScript** throughout

</td>
</tr>
</table>

---

## Getting Started

### Prerequisites

- Node.js 18+ installed
- A [Supabase](https://supabase.com) account
- An [OpenRouter](https://openrouter.ai) API key

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/amarendra-008/tweetly.git
cd tweetly
```

**2. Set up the Backend**

```bash
cd tweetly-backend
npm install
```

Create a `.env` file:

```env
PORT=3000
OPENROUTER_API_KEY=your_openrouter_api_key
SUPABASE_URL=your_supabase_project_url
SUPABASE_SERVICE_ROLE=your_supabase_service_role_key
```

Start the development server:

```bash
npm run dev
```

**3. Set up the Frontend**

```bash
cd ../tweetly-frontend
npm install
```

Create a `.env` file:

```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
VITE_API_URL=http://localhost:3000
```

Start the development server:

```bash
npm run dev
```

**4. Open your browser**

Navigate to `http://localhost:5173` and start generating tweets!

---

## Architecture

### System Overview

```
┌────────────────────────────────────────────────────────────────┐
│                         CLIENT BROWSER                          │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │                    React Application                      │  │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐   │  │
│  │  │  Landing    │  │  Create     │  │  Tweet History  │   │  │
│  │  │  View       │  │  Tweet      │  │  Component      │   │  │
│  │  └─────────────┘  └──────┬──────┘  └────────┬────────┘   │  │
│  └───────────────────────────┼─────────────────┼────────────┘  │
└──────────────────────────────┼─────────────────┼────────────────┘
                               │                 │
                               ▼                 ▼
┌──────────────────────────────────────────────────────────────────┐
│                        SUPABASE                                   │
│  ┌─────────────────────┐    ┌────────────────────────────────┐   │
│  │   Authentication    │    │         PostgreSQL DB          │   │
│  │   (Google OAuth)    │    │  ┌────────────┐ ┌───────────┐  │   │
│  └─────────────────────┘    │  │user_profiles│ │gen_tweets │  │   │
│                             │  └────────────┘ └───────────┘  │   │
│                             └────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────────┘
                               │
                               ▼
┌──────────────────────────────────────────────────────────────────┐
│                      EXPRESS BACKEND                              │
│  ┌─────────────────┐    ┌─────────────────┐    ┌──────────────┐  │
│  │   /generate     │───▶│  OpenRouter     │───▶│  Llama 3     │  │
│  │   -tweet        │    │  Service        │    │  70B Model   │  │
│  └─────────────────┘    └─────────────────┘    └──────────────┘  │
└──────────────────────────────────────────────────────────────────┘
```

### Project Structure

```
tweetly/
│
├── tweetly-frontend/              # React SPA
│   ├── src/
│   │   ├── components/            # Reusable UI components
│   │   │   ├── CreateTweet.tsx    # Main tweet generation interface
│   │   │   └── TweetHistory.tsx   # User's tweet archive
│   │   ├── views/                 # Page-level components
│   │   │   ├── LandingView.tsx    # Public homepage
│   │   │   └── TweetlyHome.tsx    # Protected dashboard
│   │   ├── lib/
│   │   │   └── supabase.ts        # Supabase client config
│   │   ├── App.tsx                # Root component & routing
│   │   └── main.tsx               # Application entry point
│   ├── package.json
│   └── vite.config.ts
│
├── tweetly-backend/               # Express REST API
│   ├── src/
│   │   ├── routes/
│   │   │   └── generate-tweet.ts  # Tweet generation endpoint
│   │   ├── services/
│   │   │   ├── openrouter.ts      # OpenRouter AI integration
│   │   │   ├── groq.ts            # Groq (future)
│   │   │   └── perplexity.ts      # Perplexity (future)
│   │   ├── lib/
│   │   │   └── supabase.ts        # Supabase admin client
│   │   └── index.ts               # Server entry point
│   └── package.json
│
└── README.md
```

---

## API Reference

### Generate Tweet

```http
POST /generate-tweet
```

**Request Body**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `userId` | string | Yes | Authenticated user's ID |
| `progress` | string | Yes | The progress update to convert |
| `tone` | string | No | `funny`, `professional`, `motivational`, `sarcastic` |
| `length` | string | No | `short`, `medium`, `thread`, `twitter-free` |

**Response**

```json
{
  "tweet": "Just shipped a feature that lets users customize their tweet tone! Building in public is the best accountability partner. 🚀"
}
```

**Example Request**

```bash
curl -X POST https://your-backend.com/generate-tweet \
  -H "Content-Type: application/json" \
  -d '{
    "userId": "user_123",
    "progress": "Finished implementing the dark mode toggle",
    "tone": "funny",
    "length": "short"
  }'
```

---

## Database Schema

### user_profiles

| Column | Type | Description |
|--------|------|-------------|
| `id` | uuid | Primary key (references auth.users) |
| `default_tone` | text | User's preferred tone |
| `default_length` | text | User's preferred length |
| `emoji_style` | text | Emoji usage preference |

### generated_tweets

| Column | Type | Description |
|--------|------|-------------|
| `id` | uuid | Primary key |
| `user_id` | uuid | Foreign key to user |
| `prompt` | text | Original progress input |
| `tweet` | text | Generated tweet content |
| `tone` | text | Tone used for generation |
| `length` | text | Length setting used |
| `created_at` | timestamp | Creation timestamp |

---

## Deployment

### Frontend (Vercel)

The frontend is configured for Vercel deployment with SPA routing:

```json
{
  "rewrites": [{ "source": "/(.*)", "destination": "/" }]
}
```

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/amarendra-008/tweetly/tree/main/tweetly-frontend)

### Backend (Railway/Render)

The backend supports Railway deployment via `railway.json`:

```json
{
  "$schema": "https://railway.com/railway.schema.json",
  "build": { "builder": "NIXPACKS" },
  "deploy": {
    "numReplicas": 1,
    "startCommand": "npm run start",
    "restartPolicyType": "ON_FAILURE"
  }
}
```

---

## Roadmap

- [ ] **Browser Extension** - Generate tweet replies directly on X/Twitter
- [ ] **Tweet Scheduling** - Schedule posts (pending Twitter API)
- [ ] **Style Learning** - AI learns your unique writing style
- [ ] **Multi-Model Support** - Switch between Groq, Perplexity, and more
- [ ] **Thread Builder** - Enhanced UI for creating tweet threads
- [ ] **Analytics Dashboard** - Track your posting patterns

---

## Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Development Guidelines

- Follow TypeScript best practices
- Use meaningful commit messages
- Add tests for new features
- Update documentation as needed

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built by [@amarendra-008](https://github.com/amarendra-008)**

</div>