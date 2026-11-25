# Residential Proxy API: What ScraperAPI Costs per 1,000 Pages, Which Plan Fits, and When Per-GB Proxies Are the Better Buy

ScraperAPI sells page requests, not gigabytes. Plans run from a free tier of 1,000 credits (capped at 5 concurrent connections) through Hobby at $49/month and Startup at $149/month for 1M credits, with rotating proxy pools, JS rendering and premium proxies bundled into every tier. On Startup a plain HTML page works out to roughly **$0.15 per 1,000 requests**. Send those same 1,000 pages through premium proxies and you pay about **$1.49**, because the credit multiplier on each request, not the plan you picked, decides your bill.

Below is the plan line-up, the credit cost of each request type converted into dollars, the two points where a bill jumps without warning, and the jobs where a per-gigabyte residential provider is the better purchase.

> **Quick pick for most readers:** use the free tier to measure your real credit cost per page, then buy Startup at $149/month for 1M credits if plain pages dominate your volume. If most of your traffic needs premium proxies or rendering, price those at 10 to 75 credits each before you commit any money. 👉 [See ScraperAPI's current plans and credit allowances](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## The plans worth comparing directly

ScraperAPI publishes one monthly price per tier plus a flat 10% discount for yearly billing. Three tiers spell out their credit allowance in the pricing page's machine-readable version, which is what makes them comparable on cost per page.

| Plan | Credits per month | Monthly price | Yearly billing (per month) | Purchase |
| --- | --- | --- | --- | --- |
| Startup | 1,000,000 | $149 | $134.10 (10% off) | [Startup plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Scaling | 5,000,000 | $475 | $427.50 ($5,130/year, saves $570) | [Scaling plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |
| Advanced | 21,500,000 (+500K bonus credits on the current offer) | $1,975 | $1,777.50 ($21,330/year, saves $2,370) | [Advanced plan](https://www.scraperapi.com/pricing/?fp_ref=coupons) |

Concurrency is where these three separate: Scaling allows 200 concurrent threads, Advanced 500, and the free tier 5.

The same page also carries Hobby at $49/month, Business at $299/month, and Professional and Enterprise tiers, each with its own allowance. 👉 [Check the full line-up and per-tier limits](https://www.scraperapi.com/pricing/?fp_ref=coupons)

## What a residential proxy API means, and which shape ScraperAPI is

A proxy API in the conventional sense is a management interface. You create sub-users, whitelist your outbound IP, set traffic caps and pull usage reports without opening a dashboard. That is how Decodo's public API works, and it ships free with any residential plan; Rapidproxy does a narrower version of the same thing, generating a ready-to-paste proxy link from parameters you set in its control panel.

ScraperAPI is the other shape. You don't manage proxy users or pick individual IPs. You send a target URL with parameters, and the service handles IP rotation, retries and block bypassing behind a single endpoint. Geotargeting, sessions, device type, output format and auto parsing are listed as zero-credit parameters, so targeting a country or holding a session doesn't consume your allowance.

That difference matters at purchase time. If your requirements include per-customer traffic quotas or choosing a specific IP from a pool, ScraperAPI doesn't expose those controls, and a proxy-management API is the right category.

## What each request costs in credits, and in dollars

Credits stack: bypassing bot protection, JS rendering and premium proxies each add their own cost on top of the base request. The dollar columns below are calculated from the published per-credit price on Startup ($149 per 1M) and Scaling ($475 per 5M).

| Request type | Credits | Cost per 1,000 on Startup | Cost per 1,000 on Scaling |
| --- | --- | --- | --- |
| Standard page | 1 | $0.15 | $0.10 |
| Amazon, Walmart, eBay | 5 | $0.75 | $0.48 |
| Bot-protection bypass (Cloudflare, DataDome, PerimeterX/HUMAN, Akamai) | +10 | +$1.49 | +$0.95 |
| JS rendering (`render=true`) | 10 | $1.49 | $0.95 |
| Premium proxies | 10 | $1.49 | $0.95 |
| Google or Bing (including subdomains) | 25 | $3.73 | $2.38 |
| Premium proxies + JS rendering | 25 | $3.73 | $2.38 |
| LinkedIn | 30 | $4.47 | $2.85 |
| Ultra premium proxies | 30 | $4.47 | $2.85 |
| Ultra premium + JS rendering | 75 | $11.18 | $7.13 |

The spread between the cheapest and most expensive row is 75×, on plans that differ by a few hundred dollars a month. That is the single most useful thing to understand before choosing a tier: a job that needs ultra premium proxies plus rendering burns through 1M credits in about 13,000 pages, not a million.

## Where the bill actually jumps

**Tier upgrades cost more than the credits do.** Pay-as-you-go is available on Scaling, Professional, Advanced and Enterprise only. On Startup and Business, running past your allowance pauses scraping unless you turn on auto-upgrade, which moves you to the next tier at full price. Overshoot Startup's 1M credits by 10% and you land on Business at $299 instead of topping up $149. If your volume sits near a boundary, trim rendering and premium proxies to the pages that genuinely need them.

**Scaling to Advanced barely changes your per-credit price.** $475 for 5M works out to $0.095 per 1,000 plain pages; $1,975 for 21.5M works out to about $0.092. A 3% improvement is not a reason to triple your spend. Upgrade for the 500 concurrent threads and the headroom, not for savings.

Yearly billing is the cleaner lever: a flat 10% off, with no separate renewal price listed. Year two costs the same as year one on the annual rate, which is not something you can assume from per-gigabyte proxy vendors running teaser first-year rates.

## Keeping the bill predictable once you're in

Every response carries an `sa-credit-cost` header showing what that request actually consumed, and the dashboard's Domain Cost Estimator tells you the cost of any URL before you scrape it. Set `max_cost` on individual scrapes so a single expensive page can't quietly drain an allowance.

Two housekeeping failures account for most first-week support tickets across this whole product category, whichever vendor you choose: an API key that can only be viewed in full at the moment you create it, and an IP whitelist that breaks the day your server's outbound address changes. Save the key somewhere durable on creation, and if your provider authenticates by whitelist rather than key, re-check the whitelist after any infrastructure move.

Concurrency is the other limit people hit before credits. Five threads on the free tier is fine for validation and painful for a production crawl; the jump to 200 requires Scaling.

## When ScraperAPI is the wrong purchase

If you want to hold a specific residential IP, swap IPs on demand, or issue traffic caps to different teams, none of that is exposed here. Decodo advertises 115M+ IPs across 195+ locations with a public API for sub-users, traffic limits and usage tracking, priced as a residential plan with the API included, plus a 3-day trial at 100MB and a 14-day money-back window. Apify bills residential traffic by the gigabyte rather than by request, pins one IP to a session ID for roughly 30 minutes, and supports country and US-state targeting. Both are built for the case where proxies are the product rather than an ingredient.

There is also a category mix-up worth flagging: IPinfo's residential proxy API detects whether an IP belongs to a proxy network, returning a `service` name and a `percent_days_seen` figure over a rolling 7-day window. It doesn't give you proxies to scrape with. If you arrived here intending to check IPs rather than route through them, that's a different tool.

## Questions that come up before buying

**Is ScraperAPI itself a residential proxy API?**
It's a scraping API with rotating proxy pools, premium proxies and ultra premium proxies included in the request price. You don't buy or manage individual residential IPs, and there's no separate proxy plan to purchase alongside the credits.

**Does geotargeting cost extra?**
No. Country-level geotargeting, sessions, device type, output format and auto parsing are all listed at zero credits. Deeper targeting than country level isn't part of the credit table.

**What happens when credits run out mid-month?**
Scraping pauses by default. You can enable auto-upgrade on Hobby, Startup, Business, Scaling and Professional, use pay-as-you-go on Scaling and above, or renew an annual plan early for a fresh batch.

**How many pages does $149 buy?**
One million plain pages, 100,000 pages at 10 credits each, or roughly 13,300 at the 75-credit ceiling. Your real number depends on which of those request types your targets trigger.

## Picking a tier

Validate on the free 1,000 credits, then let your measured credit cost per page decide. Mostly plain HTML in the hundreds of thousands per month: Startup at $149. Premium proxies on most requests: run the math at $0.95 to $1.49 per 1,000 and compare against per-gigabyte providers before paying, since the multiplier can make a $149 plan behave like a much larger one. Sustained volume past 1M credits with heavy concurrency needs: Scaling at $475, which is also the first tier where overage stops forcing a full plan upgrade.

Before you order, run your three or four hardest target domains through the Domain Cost Estimator, set `max_cost` on the scrapes you're least sure about, and decide deliberately whether auto-upgrade should be on. 👉 [Start on the free tier and size up from there](https://www.scraperapi.com/pricing/?fp_ref=coupons)
