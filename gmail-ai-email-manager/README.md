# AI Email Manager

Classifies incoming Gmail with an AI text classifier and routes each category.

**Categories:** Responder, Oportunidad, Notificacion, Marketing, Reunion, FYI. Each applies a Gmail label; important ones also send a WhatsApp alert, marketing is archived. An IF filter auto-archives dev/SaaS tool notifications, and optional Postgres lookups skip alerts for senders already handled by a lead system.

**Nodes:** Gmail Trigger (1 min poll), Text Classifier + OpenAI Chat Model, Gmail (labels/archive), IF, Postgres, HTTP Request (notifications).

**Credentials:** Gmail OAuth2, OpenAI API, HTTP Header Auth (WhatsApp API), Postgres (optional, can be removed).

**Setup:** create the 6 Gmail labels and select them in the Label nodes; replace `[YOUR_EMAIL]`, `[YOUR_PHONE_NUMBER]` and API URL placeholders; edit category descriptions for your business. The in-workflow "Setup Guide" sticky note has the full list.
