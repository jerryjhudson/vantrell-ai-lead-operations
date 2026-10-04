# Vantrell Systems — AI Lead Operations Workflow

> **Portfolio project · Fictional B2B SaaS company**  
> A Zapier-based lead operations workflow that validates inbound form data, assigns sales ownership by region, checks CRM history, uses AI to qualify and prioritize leads, and routes each outcome through controlled operational paths.

## Overview

Vantrell Systems is a fictional B2B SaaS workflow-automation company used to demonstrate a no-code/low-code AI lead-operations architecture.

The workflow is built in **Zapier** and connects **Google Forms, custom JavaScript steps, HubSpot, AI classification, Gmail, Slack, and Google Sheets**.

The system is designed to automate routine lead operations while retaining human review for ambiguous or exceptional cases.

## Business Problem

Inbound lead handling often requires several repetitive decisions before Sales can act:

- Validate and normalize form submissions
- Determine geographic ownership
- Check whether a contact already exists
- Interpret the lead's intent
- Assess priority and qualification
- Update the CRM
- Prepare follow-up communication
- Alert the correct team
- Log every outcome

Handling these steps manually adds delay and makes routing inconsistent.

## Solution

The workflow:

1. Receives a new Google Forms submission.
2. Runs JavaScript-based sanitization, normalization, and validation.
3. Splits invalid submissions into a controlled rejection/logging path.
4. Assigns a sales region and account owner using geographic business rules.
5. Searches HubSpot for an existing contact.
6. Sends the lead context to an AI qualification step.
7. Returns structured fields including:
   - AI intent
   - AI priority
   - Qualification status
   - Confidence
   - Summary
   - Recommended action
   - Human-review requirement
8. Routes the result into `Qualified`, `Needs Review`, `Unqualified`, or fallback paths.
9. Creates or updates HubSpot contacts where appropriate.
10. Creates Gmail drafts for qualified sales follow-up.
11. Applies additional priority routing for qualified leads.
12. Sends Slack alerts for high-priority leads and human-review/exception cases.
13. Writes operational outcomes to a Google Sheets run log.

## Input Validation and Sanitization

A custom JavaScript step normalizes incoming form data before AI processing.

The workflow includes controls for:

- Required fields
- Email-format validation
- Website normalization
- Text cleanup
- Spreadsheet-formula injection protection
- Inquiry-type normalization
- Validation errors and warnings

Invalid submissions are routed separately rather than continuing into sales automation.

## Geographic Routing

A custom code step assigns leads to sales regions and account owners using explicit Canada and United States state/province mappings.

This makes ownership deterministic and keeps geographic assignment outside the AI model.

## AI Qualification

The AI step classifies each valid lead using controlled output fields.

Qualification outcomes are:

- `Qualified`
- `Needs Review`
- `Unqualified`

The prompt explicitly treats the customer's message as **untrusted user-provided content** and instructs the model not to follow embedded attempts to change the workflow rules.

The model is also instructed not to invent budget, authority, timeline, company size, or other facts that were not provided.

## Human-in-the-Loop Design

Human review is required for materially ambiguous inquiries, support requests, conflicting information, and other cases that require judgment.

The workflow also includes a fallback path for unexpected AI outputs so an automation exception does not silently continue through the sales process.

## Key Capabilities

- Google Forms lead intake
- Input sanitization and validation
- Formula-injection protection for spreadsheet logging
- Geographic sales routing
- HubSpot contact lookup
- AI intent classification
- AI lead prioritization
- Lead qualification
- Confidence scoring
- CRM create/update actions
- Gmail draft creation
- Slack alerts
- Human-review and fallback paths
- Google Sheets audit logging

## Tech Stack

- Zapier
- Google Forms
- JavaScript / Code by Zapier
- HubSpot
- Zapier AI
- Gmail
- Slack
- Google Sheets
- Paths / conditional routing

## Repository Contents

- `README.md` — project overview and architecture
- `workflow.json` — sanitized portfolio export of the Zapier workflow

## Security and Sanitization

This repository contains a **sanitized portfolio export**.

Personal email addresses, Zapier account/user/authentication identifiers, Google resource IDs, Slack channel identifiers, CRM integration metadata, and other private account information have been removed or replaced with placeholders.

This export is intended as a portfolio and architecture artifact rather than a one-click deployable Zapier template. Anyone recreating the workflow must configure their own apps, credentials, fields, and resource mappings.

## Design Principles Demonstrated

- Validate before AI processing
- Deterministic ownership rules
- Structured AI outputs
- Prompt-injection awareness for user-supplied content
- Human review for uncertainty
- Fallback handling for unexpected outputs
- Draft-before-send communication
- End-to-end operational logging

## Portfolio Context

This project was created as part of my Agentic AI Automation portfolio to demonstrate practical no-code/low-code orchestration across common business applications.

**Built by Jerry J. Hudson**
