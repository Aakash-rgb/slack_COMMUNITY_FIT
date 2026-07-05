# Slack Agent

A Slack bot that monitors new members, researches them, and posts AI-generated fit analysis to a private Slack channel.

## Features
- Detects new Slack members and channel joins
- Researches member context using public data sources
- Uses OpenAI for fit analysis and recommendations
- Stores analysis results in PostgreSQL
- Posts summaries to a private Slack channel
## Architecture
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/8ef3aec1-3f24-470c-83dc-749e45439307" />

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
| Variable                   | Required | Description                                                                |
| -------------------------- | :------: | -------------------------------------------------------------------------- |
| `SLACK_BOT_TOKEN`          |     ✅    | Bot token from the Slack app (starts with `xoxb-`).                        |
| `SLACK_APP_TOKEN`          |     ✅    | App-level token for Socket Mode (starts with `xapp-`).                     |
| `SLACK_SIGNING_SECRET`     |     ✅    | Signing secret from the Slack app used to verify incoming requests.        |
| `SLACK_PRIVATE_CHANNEL_ID` |     ✅    | Slack channel ID where analysis reports are posted.                        |
| `OPENAI_API_KEY`           |     ✅    | OpenAI API key used for AI-powered analysis.                               |
| `DATABASE_URL`             |     ✅    | External PostgreSQL database connection URL (e.g., Render.com PostgreSQL). |
| `COMPANY_NAME`             |     ❌    | Company name used to provide context in AI analysis prompts.               |
| `COMPANY_PRODUCT`          |     ❌    | Product or service name used to improve AI-generated analysis.             |
| `COMPANY_WEBSITE`          |     ❌    | Company website URL for contextual information.                            |
| `COMPANY_DESCRIPTION`      |     ❌    | Brief description of the company used in AI prompts.                       |
| `NODE_ENV`                 |     ❌    | Environment mode (`development` enables debug logging and test endpoints). |
| `PORT`                     |     ❌    | Express server port (default: `3000`).                                     |

Analysis Output

## Notes
- Keep your .env file private and do not commit it.
- The project already includes a .gitignore file for this purpose.
