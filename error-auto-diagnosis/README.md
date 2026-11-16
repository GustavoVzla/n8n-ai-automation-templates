# AI Error Auto-Diagnosis

Global error workflow. Set it as the "Error Workflow" of your other workflows.

**Flow:** Error Trigger -> Prepare Error Context (Code: failed nodes, empty outputs, executed nodes, builds the prompt) -> AI Diagnose Error (OpenAI chat completions, gpt-4o-mini) -> Parse Diagnosis (Code: tolerant JSON parsing with fallback) -> WhatsApp notification (Evolution API) and HTML email (Gmail) in parallel.

**Credentials:** HTTP Header Auth for OpenAI (`Authorization: Bearer YOUR_OPENAI_API_KEY`), HTTP Header Auth for the WhatsApp API, Gmail OAuth2.

**Placeholders:** `[YOUR_EVOLUTION_API_URL]`, `[YOUR_INSTANCE_NAME]`, `[YOUR_PHONE_NUMBER]`, `[YOUR_EMAIL]`. The notification node can be replaced with Telegram or Slack.

**Import:** Workflows > Import from File > `workflow.json`, then in each monitored workflow: Settings > Error Workflow.
