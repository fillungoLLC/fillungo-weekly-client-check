# Fillungo Weekly Client Traffic Report

Automated weekly GA4 traffic report for all active clients.
Runs every Monday at 7am ET without any manual intervention.

## What it does
- Pulls 28-day session trends and 7-day channel breakdowns from GA4 for 5 properties
- Calculates week-over-week change and assigns a green/yellow/red status per property
- Flags any property outside the normal range with specific channel-level observations
- Publishes a rendered HTML report to GitHub Pages
- Posts a formatted summary with a direct link to #client-traffic-checks in Slack

## Properties tracked
- CPI (Capitol Pain Institute) — GA4 property 258891004
- Wellspring — 391071872
- Whilden — 312574658
- WMD (Wholesale Medical Devices) — 520109984
- Fillungo — 314080993

## Architecture
Google Apps Script → GA4 Data API → GitHub Pages + Slack

## Components
- `Code.gs` — the Apps Script (lives at script.google.com)
- `ga4_traffic_report.gs` — source copy saved in Internal Reporting folder
- GitHub repo: fillungoLLC/fillungo-weekly-client-check
- Published report URL: https://fillungoLLC.github.io/fillungo-weekly-client-check/
- Slack channel: #client-traffic-checks

## Schedule
Weekly trigger set in Apps Script: Monday, 7–8am ET

## Setup requirements
- Google account with Viewer access to all 5 GA4 properties
- GitHub Personal Access Token with repo scope (stored in script CONFIG)
- Slack Incoming Webhook URL for #client-traffic-checks (stored in script CONFIG)

## Modifying the script
After any code change: Deploy → Manage deployments → Edit → New version → Deploy
The GitHub Pages URL and Slack webhook do not change between versions.

## Adding a property
Add an entry to the `CONFIG.properties` array and add the name to the `order` 
array in `postToSlack()` and `buildHTML()`.
