# Real Estate CRM Pipeline + Automated Lead Alerts

A HubSpot CRM implementation for a real estate lead pipeline, with an 
instant Slack alert automation built via Zapier — designed to solve the 
#1 problem in real estate lead handling: leads going cold because no one 
follows up fast enough.

## The Problem
Real estate agents lose deals not from lack of leads, but from slow or 
missed follow-up. A lead sitting untouched for even a few hours can go 
to a competitor. This project demonstrates a CRM setup where the moment 
a lead is marked "Contacted," the assigned team gets notified instantly.

## What I Built

### 1. Custom Pipeline
A 7-stage deal pipeline modeled on a real property sales cycle:
New Lead → Contacted → Qualified → Site Visit Scheduled → Offer Made → 
Closed Won / Closed Lost

![Pipeline](screenshots/01-pipeline-stages.png)

### 2. Real-Estate-Specific Data Model
Default CRM fields don't capture what actually matters for property 
sales, so I added custom properties on both Deals and Contacts:
- Budget Range
- Property Type (Apartment / House / Plot / Commercial)
- Lead Source (Facebook Ad, Referral, Website, Instagram, Walk-in)
- Site Visit Date

![Custom Properties](screenshots/02-custom-properties.png)

### 3. Sample Data
15 contacts and deals distributed across every pipeline stage to 
simulate an active, real-world pipeline rather than an empty demo.

![Deals Board](screenshots/03-deals-board.png)

### 4. Automated Lead Alert (HubSpot → Zapier → Slack)
When a deal's stage changes, Zapier checks if it moved specifically 
into "Contacted," and if so, instantly posts a formatted alert to a 
Slack channel with the lead's budget, property type, and source — so 
whoever's online can act immediately.

**Note on scope:** HubSpot's free CRM tier does not include native 
workflow automation, and Zapier's free plan doesn't support delay 
steps. This build uses an *instant* trigger on stage change rather than 
a delayed "no activity after 3 days" trigger. In a paid HubSpot 
(Sales Hub Starter+) or Zapier (with Delay by Zapier) setup, I'd add 
a wait step + an activity-check filter to fire only when a lead has 
genuinely gone cold — this version proves the trigger → filter → 
notification logic end-to-end.

![Zap Flow](screenshots/04-zap-flow.png)
![Slack Alert](screenshots/05-slack-alert.png)

## Tools Used
HubSpot (free CRM) · Zapier (free plan) · Slack

## What I'd Add With a Paid Tier
- Delay-based "no activity in 3 days" trigger instead of instant
- Auto-assignment to specific agents based on lead source/budget
- Lead scoring based on budget + engagement
- SMS alerts alongside Slack for urgent leads
