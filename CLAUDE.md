# CLAUDE.md - AI Development Briefing

This file contains everything an AI assistant needs to work effectively on this project. **Always read this file first before making any changes.**

## Project Overview

AI-powered email automation tool for home service professionals that filters Gmail messages, generates contextual responses using HubSpot conversation history, and sends SMS drafts for mobile approval. Built with Next.js 15, Supabase, and multiple API integrations.

## Tech Stack

- **Framework**: Next.js 15 with App Router, TypeScript, Tailwind CSS
- **Database**: Supabase (PostgreSQL) with Row Level Security
- **Authentication**: Supabase Auth with role-based access
- **Integrations**: Gmail API, HubSpot API, Anthropic Claude, Twilio SMS, Make, Zapier
- **Deployment**: Vercel

## Folder Structure


app/
├── (auth)/                 # Public auth pages: login, signup
├── (dashboard)/           # Protected pages: dashboard, conversations, etc.
├── api/                   # API routes for webhooks and integrations
└── globals.css           # Global Tailwind styles

components/               # Reusable React components
├── ui/                   # Base UI components (buttons, forms, etc.)
├── forms/                # Form components
├── tables/               # Data table components
└── layouts/              # Layout components

lib/                      # Business logic and utilities only
├── integrations/         # API integration logic
├── ai/                   # AI response generation
├── sms/                  # SMS handling logic
└── utils/                # Utility functions

db/                       # Database queries and types only
├── queries/              # Supabase queries
├── types/                # Database TypeScript types
└── schema.sql           # Database schema reference

actions/                  # Server actions only
├── auth.ts              # Authentication actions
├── email.ts             # Email processing actions
└── sms.ts               # SMS handling actions

supabase/
├── migrations/          # Database migrations
└── config.ts            # Supabase client configuration


## Coding Conventions

- **TypeScript**: Strict mode enabled, explicit types required
- **Components**: Server components by default, use 'use client' only when necessary
- **Data Access**: All database queries go in `/db` directory only
- **Business Logic**: Complex logic goes in `/lib` or `/actions`, not in components
- **Client Security**: Never put secrets, API keys, or sensitive logic in client components
- **Error Handling**: Use proper try/catch blocks and return structured error responses
- **Styling**: Tailwind CSS with consistent design system

## Current State - What's Built

This is a fresh scaffold with:
- ✅ Next.js 15 project structure with App Router
- ✅ Supabase integration with authentication
- ✅ Database schema with 11 tables (migrations created)
- ✅ Route stubs for all 13 pages from site map
- ✅ Basic component structure
- ✅ Integration stubs for Gmail, HubSpot, Claude, Twilio, Make, Zapier
- ✅ TypeScript configuration
- ✅ Tailwind CSS setup

**Nothing functional is built yet** - all routes return placeholder content.

## What to Build Next - v1 Features

1. **SMS draft approval system** - Simple yes/no SMS responses that trigger email sending via Gmail API
2. **Gmail message filtering** - Filter incoming emails by recipient with conversation threading
3. **HubSpot CRM integration** - Pull contact history and context for AI response generation
4. **Anthropic Claude integration** - Generate contextual email responses based on conversation data

Start with the core workflow: Gmail webhook → filter → generate response → send SMS → handle approval → send email.

## Never Touch Rules

- **Never modify** `.env` files without explicit instruction
- **Never modify** migration files without explicit instruction - create new ones instead
- **Never modify** RLS policies without security review
- **Never commit** API keys, secrets, or sensitive data
- **Never bypass** TypeScript errors - fix them properly

## How to Work on This Project

1. **Always read this file first** before making any changes
2. **Run `npm run build`** before committing to catch errors
3. **Commit small and often** with conventional commit messages:
   - `feat:` new features
   - `fix:` bug fixes  
   - `refactor:` code improvements
   - `docs:` documentation updates
4. **Document technical debt explicitly** in TECHNICAL_DEBT.md
5. **Test integrations thoroughly** - this project has complex external dependencies
6. **Mobile-first design** - the user needs to approve SMS drafts on their phone

## Integration Notes

- **Gmail**: Use Gmail API for reading and sending, webhooks for real-time updates
- **HubSpot**: REST API for contact/conversation data, consider rate limiting
- **Claude**: Use for contextual response generation, implement retry logic
- **Twilio**: SMS for draft approval, webhook for response handling
- **Make/Zapier**: Optional automation endpoints for power users

## Security Considerations

- All email content is sensitive - implement proper encryption
- API credentials must be server-side only
- RLS policies protect user data isolation
- SMS approvals need verification to prevent spoofing
- Gmail OAuth scopes should be minimal necessary permissions