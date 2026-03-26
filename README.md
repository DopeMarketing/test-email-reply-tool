# test - email reply tool

AI-powered email automation tool that filters Gmail messages, generates contextual responses using conversation history, and sends SMS drafts for mobile approval.

## What This Does

This tool automates email response workflows for home service professionals by:
- Filtering incoming Gmail messages by recipient
- Pulling conversation context from HubSpot CRM
- Generating AI-powered email responses using Anthropic Claude
- Sending draft responses via SMS for yes/no approval
- Automatically sending approved responses through Gmail

## Who This Is For

Built for home service business owners who need to manage email communications efficiently while working in the field.

## Tech Stack

- **Framework**: Next.js 15 with App Router
- **Database**: Supabase (PostgreSQL)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Authentication**: Supabase Auth
- **Deployment**: Vercel
- **Integrations**: Gmail API, HubSpot API, Anthropic Claude, Twilio SMS, Make, Zapier

## Prerequisites

- Node.js 18+ and npm
- Supabase CLI
- Gmail API credentials
- HubSpot API key
- Anthropic API key
- Twilio account credentials

## Local Development Setup

1. **Clone the repository**
   bash
   git clone <repository-url>
   cd test-email-reply-tool
   

2. **Install dependencies**
   bash
   npm install
   

3. **Set up environment variables**
   bash
   cp .env.example .env.local
   
   Fill in the required environment variables (see table below).

4. **Start Supabase locally**
   bash
   supabase start
   

5. **Run database migrations**
   bash
   supabase db reset
   

6. **Start the development server**
   bash
   npm run dev
   

7. **Open your browser**
   Navigate to `http://localhost:3000`

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase project URL | Yes |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Supabase anonymous key | Yes |
| `SUPABASE_SERVICE_ROLE_KEY` | Supabase service role key | Yes |
| `GMAIL_CLIENT_ID` | Google OAuth client ID | Yes |
| `GMAIL_CLIENT_SECRET` | Google OAuth client secret | Yes |
| `HUBSPOT_API_KEY` | HubSpot private app API key | Yes |
| `ANTHROPIC_API_KEY` | Anthropic Claude API key | Yes |
| `TWILIO_ACCOUNT_SID` | Twilio account SID | Yes |
| `TWILIO_AUTH_TOKEN` | Twilio auth token | Yes |
| `TWILIO_PHONE_NUMBER` | Twilio phone number | Yes |
| `MAKE_WEBHOOK_URL` | Make.com webhook URL | No |
| `ZAPIER_WEBHOOK_URL` | Zapier webhook URL | No |
| `NEXTAUTH_SECRET` | NextAuth secret key | Yes |
| `NEXTAUTH_URL` | Application URL | Yes |

## Database Setup

The database schema includes 11 tables:
- `auth_users` - User authentication
- `api_integrations` - API connection settings
- `email_filters` - Gmail filtering rules
- `gmail_messages` - Incoming email data
- `conversation_threads` - Email thread tracking
- `hubspot_contacts` - CRM contact sync
- `ai_response_drafts` - Generated email responses
- `sms_approvals` - SMS approval tracking
- `sms_responses` - SMS reply handling
- `sent_emails` - Outbound email log
- `automation_logs` - System activity tracking

Run `supabase db reset` to set up the initial schema.

## Deploy to Vercel

1. **Connect your repository to Vercel**
2. **Set environment variables** in the Vercel dashboard
3. **Deploy**
   bash
   npm run build
   git push origin main
   

## Project Structure


├── app/                    # Next.js app directory
│   ├── (auth)/            # Authentication routes
│   ├── (dashboard)/       # Protected dashboard routes
│   ├── api/               # API routes
│   └── globals.css        # Global styles
├── components/            # Reusable React components
├── lib/                   # Business logic and utilities
├── db/                    # Database queries and types
├── actions/               # Server actions
├── types/                 # TypeScript type definitions
├── supabase/              # Supabase configuration and migrations
└── public/                # Static assets
