WhatsApp AI Order Agent (Multimodal)

Overview
A no-code AI-powered WhatsApp business assistant capable of:
Processing text, voice, and image inputs
Extracting structured order data from free text
Automatically calculating total pricing
Reading product/menu data from Airtable
Writing customer orders back to Airtable
Responding instantly via WhatsApp Cloud API
Built using n8n as orchestration engine with Google Gemini multimodal models.

Architecture
Customer (WhatsApp)
        ↓
Meta WhatsApp Cloud API
        ↓
Webhook (n8n Trigger)
        ↓
Switch Node (Text / Image / Audio)
        ↓
[Audio Flow]
  → Get Media URL
  → Download Audio
  → Gemini Transcription
  → AI Agent

[Image Flow]
  → Get Media URL
  → Download Image
  → Gemini Vision Analysis
  → AI Agent

[Text Flow]
  → AI Agent

AI Agent (Gemini Chat Model)
        ↓
Airtable (Search Records)
        ↓
Airtable (Create Order Record)
        ↓
WhatsApp Response

Order Processing Logic


The AI Agent:
Parses customer message
Extracts structured fields:
Customer name
Address
Product
Quantity
Reads menu data from Airtable
Calculates total price dynamically
Writes structured order record into Airtable
Sends confirmation response via WhatsApp
Total pricing is calculated by the AI Agent using product data retrieved from Airtable.
