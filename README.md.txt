🚀 DomainSwitcher: Automated Domain Recovery System
DomainSwitcher is an intelligent automation designed to drastically reduce downtime caused by domain blocks. It monitors, identifies, and replaces blocked domains in MyAffiliates (Throne & Realm) using a headless browser worker and real-time Slack/Monday.com synchronization.

📑 Table of Contents
Architecture

Tech Stack

Key Features

Monday.com Integration

Setup & Installation

🏗 Architecture
The system operates through a distributed architecture:

Triggers: Marketing block notifications arrive via Webhooks or Monday.com status changes.

Logic Engine (n8n): Orchestrates the decision-making process, looks up backup domains, and updates statuses.

Execution Worker (Railway): A Node.js/Playwright server that performs the actual Search & Replace inside MyAffiliates instances.

Communication (Slack): Provides real-time status updates and critical alerts to the team.

🛠 Tech Stack
n8n: Workflow automation and data transformation.

Node.js & Playwright: Headless browser automation hosted on Railway.

Monday.com API: Inventory management for backup domains.

Slack API: Interactive notifications and error logging.

✨ Key Features
Intelligent Backup Selection: A custom JavaScript algorithm filters the best backup domain by Brand and Type, ensuring 100% accuracy.

Automated Inventory Update: Once a backup is picked, the system automatically marks it as Active in Monday.com to prevent duplicates.

24/7 Keep-Alive: A scheduled task calls /refresh every 10 minutes to keep MyAffiliates sessions active without manual logins.

Cross-Instance Support: Full compatibility with both Throne and Realm environments.

📊 Monday.com Integration
The system expects specific Column IDs to function correctly in the Realm board:

Brand: dropdown_mkr0c2a9.

Type: color_mkr4v8y2 (Used for Bridge/Ad-Server filtering).

Status: color_mkr0zqkc (Automatically updated to { "label": "Active" }).

🚀 Setup & Installation
Railway Worker
Clone the /server directory.

Set environment variables for USER_THRONE, PASS_THRONE, USER_REALM, and PASS_REALM.

Deploy to Railway and ensure Playwright dependencies are installed.

n8n Workflow
Import the JSON files located in the /workflows folder.

Update the HTTP Request nodes with your Railway App URL.

Set your Slack Member ID (e.g., D070K8NGLHF) in the notification nodes to receive private alerts.

📝 Current Scope
✅ Bridge Domains: Fully automated Search & Replace.

🚧 Ad-Server Domains: Currently in development.