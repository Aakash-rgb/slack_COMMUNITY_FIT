# Slack Agent

A Slack bot that monitors new members, researches them, and posts AI-generated fit analysis to a private Slack channel.

## Features
- Detects new Slack members and channel joins
- Researches member context using public data sources
- Uses OpenAI for fit analysis and recommendations
- Stores analysis results in PostgreSQL
- Posts summaries to a private Slack channel

## Setup
1. Install dependencies:
   npm install
2. Create a .env file with your Slack, OpenAI, and database configuration.
3. Start the app:
   npm start

## Notes
- Keep your .env file private and do not commit it.
- The project already includes a .gitignore file for this purpose.
