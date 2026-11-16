# AI Email Proactive Responder

Sub-workflow (Execute Workflow Trigger) that prepares reply drafts for emails from known leads.

**Flow:** Trigger -> Extract Sender Email -> Lookup Lead (Postgres) -> Is Known Lead? -> AI Analyze Email (OpenAI-compatible API, JSON output) -> Parse AI Response -> Build MIME Message -> Create Gmail Draft (Gmail API) -> Save Pending Action (Postgres) -> Notify Owner. Nothing is sent automatically: the owner reviews the draft.

**Credentials:** PostgreSQL, HTTP Header Auth (OpenAI), Gmail OAuth2, HTTP Header Auth (notification API).

**Placeholders:** `[YOUR_BUSINESS]`, `[YOUR_NAME]`, `[YOUR_PHONE]`, `[YOUR_NOTIFICATION_API_URL]`. Expected table schemas (`leads_handoff`, `negocios`, `acciones_pendientes`) are described in the `_comment` of the Postgres nodes; adapt the queries to your own schema.

**Import:** call it from another workflow (for example the Gmail manager) passing the email object.
