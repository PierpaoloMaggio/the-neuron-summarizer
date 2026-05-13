# The Neuron Summarizer

GitHub Actions cron che ogni ora controlla il feed RSS del canale YouTube The Neuron, estrae la trascrizione del video tramite Apify, ne produce un riassunto in italiano via Claude Sonnet 4.5 (OpenRouter) e invia un'email a Pierpaolo.

Stesso pattern di `lenny-podcast-summarizer`.

## Secrets richiesti

- `APIFY_TOKEN`
- `OPENROUTER_KEY`
- `GMAIL_USER`
- `GMAIL_APP_PASSWORD`

## Comportamento

- Cron orario (`0 * * * *`) e `workflow_dispatch` manuale.
- Primo run: seed dello stato con i videoId correnti senza processare nulla.
- Run successivi: processa solo nuovi videoId non ancora in `state.json`.
- Filtra titoli con `#shorts` e trascrizioni `<1500` caratteri.
- Lista `processed` capped a 200 elementi.

## Canale

The Neuron — `UCnqfe58aUR8N3D2LV6lEoJQ` — https://www.youtube.com/@theneuronai
