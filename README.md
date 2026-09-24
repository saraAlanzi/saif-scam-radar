# Saif Scam Radar

A cybersecurity platform concept that stops online fraud at its source.
Victims report suspicious messages. The system extracts links, phone numbers and bank accounts, then links reports that share them into one scam campaign, so a single account can be flagged for every victim at once.

Built for the Security & Innovation Fair (SAIF) 2026. Category: Cybersecurity & Defense Technologies. Type: system / platform. Stage: prototype.

## What is in this repository

- `index.html` - interactive prototype (single file, no install). Open it in any browser.

## What the prototype shows

- **Message check:** paste a scam message to see a risk score, the extracted links / phone numbers / bank accounts, and whether the account matches a known campaign.
- **Parallel processing:** a slider showing how splitting reports across workers reduces processing time.
- **Campaign view:** reports linked by shared bank accounts.

## Honest scope

This is a prototype. The message check uses simple rules (keyword and link patterns) running in the browser, and the campaign data and the speed-up numbers are **synthetic / illustrative**, not measured results. No real victim or account information is used.

## Planned architecture

1. Collect reports
2. Extract entities (links, phones, bank accounts)
3. Connect reports that share an entity into campaigns
4. Act: live blocklist and a summary for banks

Reports are partitioned by shared entity so a campaign is never split across workers, then processed in parallel (Python `multiprocessing`) and merged.

## Future work

- Measured benchmark on 500,000 synthetic reports: sequential vs parallel
- Near-duplicate message matching and fake-domain detection
- Bank and authority reporting workflow
- Arabic message support
