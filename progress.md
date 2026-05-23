## Day 1 — Foundation Complete

### What's done
- n8n running locally via Docker with persistent volume
- Google Sheets OAuth connected — reading client and market card data
- Gemini 2.5 Flash API key working
- End-to-end validation: n8n reads Acme Cloud profile + Germany market card → Gemini generates German ad copy
- Three client profiles authored (Acme Cloud, GreenLeaf Organics, TechReach Edu)
- Germany market card authored with UWG-grounded cultural notes

### Sample output (Acme Cloud × Germany)
Headline: "Parallel Deploys: 11 Min. auf 11 Sek."
Description: "Verkürzen Sie Ihre Bereitstellungszeiten um den Faktor 60."

### Notes
- Gemini 2.0 Flash has rate limits on free tier — using 2.5 Flash instead
- Anthropic deferred (no free tier) — will add as fallback on Day 4
- Model wraps output in markdown code fences despite instructions — will add cleanup step Day 2

### Tomorrow (Day 2)
- Author remaining 3 market cards (Brazil, Japan, India)
- Engineer the prompt properly with dynamic expressions
- First structured output with schema enforcement

## Day 2 — Dynamic Expressions + Multi-Client Testing

### What's done
- Authored three additional market cards: Brazil (pt-BR), Japan (ja-JP), India (en-IN)
- Replaced hardcoded prompt with Code node that dynamically builds prompt from Sheets data
- Wired HTTP Request to use dynamically-built JSON body
- Tested system across multiple client × market combinations:
  - Acme Cloud × Germany: technical, confident, UWG-compliant German
  - GreenLeaf Organics × Brazil: warm, relational, Brazilian Portuguese
  - TechReach Edu × Japan: indirect, trust-focused, polite Japanese register
  
All three outputs demonstrated proper cultural adaptation and brand voice matching without prompt changes.

### System architecture now complete
- n8n workflow: fully dynamic
- Client profiles: 3 (Acme Cloud, GreenLeaf Organics, TechReach Edu)
- Market cards: 4 (Germany, Brazil, Japan, India) with cultural research
- Prompt generation: Code node with expression-based string interpolation
- LLM calls: Gemini 2.5 Flash with structured JSON output

### Next (Day 3)
- Add Claude Haiku fallback (requires $5 Anthropic top-up)
- Implement deterministic post-checks (banned terms, char count, glossary)
- Build error handling and retry logic
- Test edge cases and failure modes
