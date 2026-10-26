# FreshRoute · AI Ops Dashboard

An operations dashboard for a grocery delivery start-up in Barcelona, Madrid and Valencia. It uses an LLM (Claude, via OpenRouter) to make the decisions the ops team was making by hand in spreadsheets and WhatsApp.

![Substitution engine](screenshots/substitution-engine.png)

## The problem

FreshRoute's customer rating had dropped from 4.6 to 4.1 in six months. 22% of complaints were about poor substitutions, and the average delivery took 47 minutes, about 15 minutes slower than competitors. The dashboard tackles the four causes behind those numbers.

## What it does

| Module | What the AI does |
|---|---|
| **AI Substitutions** | When an item is out of stock, recommends a replacement that fits the customer's diet, budget and history, with a confidence score and two alternatives. |
| **Route Optimiser** | Groups pending orders and assigns them to the nearest available rider on a live map of Barcelona. |
| **Demand Forecast** | Predicts next week's demand for key products and flags stores that need to restock. |
| **Inventory** | Compares stock with predicted demand and turns the gaps into supplier orders. |

Every AI decision updates the KPI cards (rating, complaint rate, decisions today), so you can see the business effect of each one.

## Try it

Open `index.html` in a browser.

- **Demo mode (default):** without an API key, each module shows realistic simulated results, clearly labelled **Simulated**.
- **Live mode:** paste an [OpenRouter](https://openrouter.ai) key into the box in the sidebar. The key stays in that browser tab only and is never saved to the code.

If live calls are blocked when the file is opened directly, serve the folder instead:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

## Built with

HTML, CSS, vanilla JavaScript · Claude Haiku 4.5 via the OpenRouter API · Leaflet + OpenStreetMap for the route map · Canvas sparklines

## How the AI is used

Each module builds a structured prompt from the scenario data (customer profile, order, rider positions, order history) and asks the model to reply in strict JSON. The page parses that JSON and renders it as cards, routes and alerts. If the call fails or there is no key, the module falls back to a simulated result instead of breaking.

## Notes

The stores, customers and figures are fictional and were created for a university case study.
