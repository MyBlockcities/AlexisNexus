# Alexis Nexus AI Social Agent

An intelligent AI agent designed for automated content curation, analysis, and social media engagement, focusing on AI and cryptocurrency topics.

## Overview

Alexis Nexus is a sophisticated AI agent that combines multiple services to create an engaging social media presence. The system aggregates content from various sources, analyzes sentiment and trends, generates engaging posts, and manages social media interactions across platforms.

### Core Features

- **Content Aggregation**
  - News collection from multiple sources (NewsAPI)
  - Reddit content monitoring and interaction
  - Customizable topic tracking
  - Smart content filtering and ranking

- **Content Analysis**
  - Sentiment analysis using OpenAI GPT-4
  - Keyword extraction and trend identification
  - Engagement potential scoring
  - Content relevance ranking

- **Content Generation**
  - AI-powered post creation
  - Multi-platform content adaptation
  - Automated response generation
  - Contextual thread creation

- **Engagement Management**
  - Real-time engagement monitoring
  - Automated response scheduling
  - Trend analysis and alerting
  - Performance analytics

- **Scheduling System**
  - Intelligent post timing
  - Queue management
  - Cross-platform coordination
  - Workload distribution

## Installation

### Prerequisites

- Node.js 16.x or higher
- pnpm package manager
- OpenAI API access
- NewsAPI account
- Reddit API credentials

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/alexis-nexus.git
cd alexis-nexus
```

2. Install dependencies:
```bash
pnpm install
```

3. Create environment file:
```bash
cp .env.template .env
```

4. Configure environment variables:

### Required Environment Variables

```env
# API Keys
NEWS_API_KEY=your_newsapi_key
OPENAI_API_KEY=your_openai_key

# Reddit API Credentials
REDDIT_CLIENT_ID=your_reddit_client_id
REDDIT_CLIENT_SECRET=your_reddit_client_secret
REDDIT_USERNAME=your_reddit_username
REDDIT_PASSWORD=your_reddit_password

# Content Settings
CONTENT_CACHE_DURATION=3600000
UPDATE_INTERVAL=1800000
DEBUG_MODE=true

# Rate Limiting
MAX_REQUESTS_PER_MINUTE=30
REQUEST_INTERVAL=2000

# Monitoring
ENABLE_ERROR_LOGGING=true
ERROR_LOG_PATH=./logs/error.log

# Feature Flags
ENABLE_SENTIMENT_ANALYSIS=true
ENABLE_KEYWORD_EXTRACTION=true
ENABLE_AUTO_POSTING=false
```

## Usage

### Starting the Agent

1. Basic start:
```bash
pnpm start
```

2. Development mode:
```bash
pnpm dev
```

3. With specific configuration:
```bash
pnpm start -- --config custom-config.json
```

### Configuration

Create a configuration file (config.json):

```json
{
  "scheduling": {
    "postingInterval": 3600,
    "maxPostsPerDay": 24,
    "workingHours": {
      "start": 9,
      "end": 22
    }
  },
  "monitoring": {
    "checkInterval": 300000
  },
  "content": {
    "minScoreThreshold": 0.7,
    "subreddits": [
      "artificial",
      "MachineLearning",
      "cryptocurrency"
    ]
  }
}
```

## Architecture

### Service Structure

```
src/
├── services/
│   ├── newsAPI.ts           # News aggregation
│   ├── redditAPI.ts         # Reddit interaction
│   ├── contentAnalysis.ts   # Content analysis
│   ├── contentScheduler.ts  # Scheduling system
│   ├── engagementMonitor.ts # Engagement tracking
│   └── contentOrchestrator.ts # Main orchestrator
├── types/
│   └── index.ts            # Type definitions
├── config/
│   └── apis.ts             # API configurations
└── examples/
    └── contentAggregation.ts # Usage examples
```

### Main Components

1. **Content Aggregator**
   - Fetches and combines content from multiple sources
   - Implements caching and rate limiting
   - Handles content filtering and initial ranking

2. **Content Analysis**
   - Performs sentiment analysis
   - Extracts keywords and topics
   - Calculates engagement potential
   - Generates content scores

3. **Content Scheduler**
   - Manages posting queue
   - Implements timing strategies
   - Handles cross-platform coordination
   - Monitors posting limits

4. **Engagement Monitor**
   - Tracks post performance
   - Generates engagement alerts
   - Analyzes trends
   - Provides performance metrics

## Extending the System

### Adding New Content Sources

1. Create a new service class:
```typescript
export class NewSourceService {
  constructor(credentials: any) {
    // Initialize service
  }

  async fetchContent(): Promise<any> {
    // Implement content fetching
  }
}
```

2. Update the ContentAggregator:
```typescript
this.sources.push(new NewSourceService(credentials));
```

### Adding New Platforms

1. Create platform-specific client:
```typescript
export class PlatformClient {
  async post(content: any): Promise<any> {
    // Implement posting
  }

  async monitor(postId: string): Promise<any> {
    // Implement monitoring
  }
}
```

2. Update the ContentOrchestrator:
```typescript
this.platforms.set('platform_name', new PlatformClient());
```

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details