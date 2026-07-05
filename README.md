# Slack Agent

A Slack bot that monitors new members, researches them, and posts AI-generated fit analysis to a private Slack channel.

## Features
- Detects new Slack members and channel joins
- Researches member context using public data sources
- Uses OpenAI for fit analysis and recommendations
- Stores analysis results in PostgreSQL
- Posts summaries to a private Slack channel
## Architecture
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Slack API     │───▶│  Slack Service   │───▶│ Member Research │
│ (New Members)   │    │  (Event Handler) │    │    Service      │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                                                          │
                                                          ▼
                                                ┌─────────────────┐
                                                │ OpenAI/Langchain│
                                                └────────┬────────┘
                                                         │
                       ┌──────────────────┐              │
                       │  Analysis Report │◀─────────────┘
                       │   Generator      │
                       └───────┬──────────┘
                               │
                    ┌──────────┴──────────┐
                    ▼                     ▼
          ┌─────────────────┐   ┌─────────────────┐
          │   PostgreSQL    │   │ Private Channel │
          │  (Render.com)   │   │  (Slack Bot)    │
          └─────────────────┘   └─────────────────┘
## Prerequisites
Node.js 18+
OpenAI API key
Slack workspace with admin access
Render.com account (for deployment and database)

## Setup
1. Install dependencies:
   npm install
2. Create a .env file with your Slack, OpenAI, and database configuration.
3. Start the app:
   npm start
## Environment Variables
Variable	               Required	       Description
SLACK_BOT_TOKEN	        ✅	          Bot token from Slack app (starts with xoxb-)
SLACK_APP_TOKEN	        ✅	          App-level token for Socket Mode (starts with xapp-)
SLACK_SIGNING_SECRET	     ✅	          Signing secret from Slack app
SLACK_PRIVATE_CHANNEL_ID  ✅	          Channel ID where reports are sent
OPENAI_API_KEY	           ✅	          OpenAI API key
DATABASE_URL	           ✅	          Render.com PostgreSQL external database url
COMPANY_NAME	           ❌	          Your company name (used in AI analysis prompt)
COMPANY_PRODUCT	        ❌	          Your product name (used in AI analysis prompt)
COMPANY_WEBSITE	        ❌	          Your company website URL
COMPANY_DESCRIPTION	     ❌	          Brief description of your company
NODE_ENV	                 ❌	          Set to development to enable debug logging and test endpoint
PORT	                    ❌	          Express server port (default 3000)
Analysis Output

## Notes
- Keep your .env file private and do not commit it.
- The project already includes a .gitignore file for this purpose.
