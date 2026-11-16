# n8n AI Automation Templates

Three production-style n8n workflows that combine LLMs with real business tooling (Gmail, PostgreSQL, WhatsApp/Telegram/Slack notifications). All credentials, IDs and endpoints are replaced with placeholders, so each workflow imports cleanly into any n8n instance.

Built by **Gustavo Tejera**.

## Workflows

| Folder | What it does | Key nodes |
|---|---|---|
| [`error-auto-diagnosis`](error-auto-diagnosis) | Global error handler: when any workflow fails, it collects the execution context (failed nodes, silent empty outputs), asks an LLM for root cause, severity and a concrete fix, then notifies by WhatsApp and email. | Error Trigger, Code, HTTP Request (OpenAI), Gmail |
| [`gmail-ai-email-manager`](gmail-ai-email-manager) | Polls unread Gmail, classifies each email into 6 categories with an AI text classifier, applies labels, auto-archives marketing/tool noise and pushes WhatsApp alerts for what needs attention. | Gmail Trigger, Text Classifier + OpenAI Chat Model, IF, Postgres, Gmail |
| [`email-proactive-responder`](email-proactive-responder) | Looks up the sender in a leads table; for known leads an LLM analyzes the email and a reply is written as a Gmail draft (raw MIME built in code), stored as a pending action and sent to the owner for review. A human stays in the loop. | Execute Workflow Trigger, Postgres, IF, HTTP Request (LLM), Code, Gmail API |

## Skills shown

- **AI agents and LLM integration:** classification chains, structured JSON output with robust parsing and fallbacks, prompt design with business context.
- **Error handling:** dedicated error workflow, `onError: continueRegularOutput` on non-critical branches, detection of silent failures (nodes with empty output).
- **Integrations:** Gmail (OAuth2 and raw API), PostgreSQL, OpenAI-compatible APIs, WhatsApp via Evolution API (swappable for Telegram or Slack).
- **Workflow design:** sub-workflow triggers, human-in-the-loop approval, SQL escaping in code nodes, setup notes embedded as sticky notes and `_comment` fields.
- **Triggers:** polling trigger, error trigger, execute-workflow trigger.

## Importing

1. In n8n: Workflows > Import from File > pick a `workflow.json`.
2. Create the credentials listed in that folder's README and select them in the nodes.
3. Search the JSON for `YOUR_` to find every placeholder to replace.
4. Run with test data before activating.

These templates are examples: review the prompts, SQL schemas and notification targets before using them with real data.

## License

MIT, see [LICENSE](LICENSE).

---

## Resumen en español

Tres workflows de n8n con IA, listos para importar y sin datos sensibles: diagnóstico automático de errores con LLM, gestor de Gmail con clasificación por IA y respuestas proactivas en borrador con revisión humana. Muestran agentes IA, manejo de errores, integraciones (Gmail, PostgreSQL, WhatsApp) y diseño de flujos. Autor: Gustavo Tejera.
