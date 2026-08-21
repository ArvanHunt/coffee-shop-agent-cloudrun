# Coffee Shop Agent — Cloud Run + ADK

An AI business analyst agent for a coffee shop, built with Google's Agent Development Kit (ADK) and deployed on Cloud Run with sandbox execution.

## What it does
- Reads historical POS (point-of-sale) data from a Google Sheet
- Correlates past sales spikes with a graduation ceremony schedule
- Uses a secure Cloud Run sandbox to run Python analysis scripts
- Recommends staffing and inventory adjustments via a chat UI
- Writes approved tasks to a "TODO" tab in the spreadsheet (human-in-the-loop)

## Stack
- FastAPI + WebSockets for the chat UI
- Google ADK (Agent Development Kit)
- Cloud Run sandbox for code execution
- Google Sheets API for data read/write
- Deployed on Cloud Run (asia-south1)

## Setup
1. Set environment variables: GOOGLE_CLOUD_PROJECT, REGION, SPREADSHEET_ID
2. Create a service account with roles/aiplatform.user and Sheets Editor access to your spreadsheet
3. Deploy with:

gcloud beta run deploy coffee-mgr-agent \
    --source=. \
    --region=$REGION \
    --sandbox-launcher \
    --allow-unauthenticated \
    --service-account $SERVICE_ACCOUNT_ADDRESS \
    --set-env-vars GOOGLE_GENAI_USE_VERTEXAI=1,GOOGLE_CLOUD_PROJECT=$GOOGLE_CLOUD_PROJECT,SPREADSHEET_ID=$SPREADSHEET_ID

Built as part of Google Gen AI Academy APAC (Cohort 3), Track 3.
