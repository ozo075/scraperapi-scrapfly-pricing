# scraperapi vs scrapfly: which one clears your target list, what 1,000 pages really cost, and which plan to buy (full ScraperAPI price table)

There is no overall winner, and the gap between these two is wide enough that the wrong pick shows up on your invoice inside a month. ScraperAPI starts at $49/month for 100,000 credits; Scrapfly starts at $30/month for 200,000. Neither number means much on its own, because both platforms bill in credits and the credit cost of a single page moves between 1 and 75 depending on what you point it at.

What follows is the arithmetic behind that range, the per-site success rates from the most recent public benchmark (October 1 to November 1, 2026), and the plan each volume band should buy.

## Quick picks

- **Amazon, Walmart, eBay, Zillow or Google SERPs, with parsed JSON in the response:** ScraperAPI Business, $299/month for 3,000,000 credits, 100 concurrent threads, country-level geotargeting.
- **Under ~1M credits a month:** ScraperAPI Hobby at $49 or Startup at $149. Both are US and EU geotargeting only.
- **Booking, Indeed, Realtor, StockX, Instagram or Twitter on the list:** Scrapfly wins those by a distance. Its October run scored 74.7% to 99.3% on them against 36.8% to 97.2% for ScraperAPI.

👉 [Start ScraperAPI's 7-day trial, 5,000 credits, no card required](https://www.scraperapi.com/?fp_ref=coupons)

## ScraperAPI plans and prices

Seven tiers, all monthly by default, with a flat 10% off if you switch to annual billing. Every paid plan includes JS rendering, premium proxies, CAPTCHA handling, automatic retries, custom headers and sessions, desktop and mobile user agents, and a 99.9% uptime guarantee.

| Plan | Monthly price | Annual (per month) | Credits | Concurrency | Get started |
| --- | --- | --- | --- | --- | --- |
| Hobby | $49 | $44.10 | 100,000 | 20 | [Start trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Startup | $149 | $134.10 | 1,000,000 | 50 | [Start trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Business | $299 | $269.10 | 3,000,000 | 100 | [Start trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Scaling | $475 | $427.50 | 5,000,000 | 200 | [Start trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Professional | $975 | $877.50 | 10,500,000 | 300 | [Start trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Advanced | $1,975 | $1,777.50 | 21,500,000 | 500 | [Start trial](https://www.scraperapi.com/?fp_ref=coupons) |
| Enterprise | Custom | Custom | 22M+ | 500+ | [Talk to sales](https://www.scraperapi.com/?fp_ref=coupons) |

Three details the table hides:

**Geotargeting is tiered.** Hobby and Startup are US and EU only. Country-level targeting starts at Business ($299). If your project needs Brazilian or Japanese exit IPs, the $49 and $149 plans cannot do it at any configuration.

**Credits reset, they do not roll over.** Unused credits disappear at renewal. When the balance hits zero, scraping pauses rather than billing you for more. Two escape hatches exist, and they are not available everywhere: auto-upgrade (opt-in, moves you to the next tier mid-cycle) works on Hobby through Professional, while true pay-as-you-go at a fixed per-credit rate only starts at Scaling. On Hobby and Startup your choices are pause or jump a whole tier.

**Concurrency overruns are rejected, not queued.** Exceed your thread limit and you get a 429 back. No extra charge, no request.

Annual billing on Hobby works out to $529.20 for the year against $588 monthly, a $58.80 saving. The discount is identical at every tier, so the real reason to annualise is not the 10%, it's knowing your volume.

## What a page actually costs

This is where the two platforms diverge, and where most comparisons stop short.

ScraperAPI's base unit is 1 credit for a standard page. The documented multipliers stack on top:

| What you're scraping | Credits per request |
| --- | --- |
| Standard HTML page | 1 |
| Amazon (also 5 for Walmart, eBay e-commerce logic) | 5 |
| Google or Bing SERP | 25 |
| LinkedIn | 30 |
| JS rendering (`render=true`) | +10 |
| Residential proxy (`premium=true`) | +10 |
| Ultra premium proxy (`ultra_premium=true`) | +30 |
| Residential proxy plus JS rendering | +25 (not +20) |
| Ultra premium plus JS rendering | +75 (not +40) |
| Bypassing Cloudflare, DataDome or PerimeterX (auto-detected) | +10 each |

Run those through the credit rates of two plans and the "cheap" tiers stop looking cheap:

| Target type | Credits/page | Hobby ($49 / 100K) | Business ($299 / 3M) |
| --- | --- | --- | --- |
| Standard HTML | 1 | $0.49 / 1K | $0.10 / 1K |
| Amazon product page | 5 | $2.45 / 1K | $0.50 / 1K |
| Google SERP | 25 | $12.25 / 1K | $2.49 / 1K |
| Protected site (ultra premium + JS) | 75 | $36.75 / 1K | $7.48 / 1K |

A Hobby plan pointed at Cloudflare-protected pages buys roughly **1,333 actual page loads**, not 100,000. The same 3M credits on Business buy 40,000, and the per-page cost falls by a factor of five. If your targets are hard, the plan tier matters more than the vendor.

Scrapfly's multipliers run the other way for the nasty stuff: 1 credit basic, 5 with JS rendering, 25 with residential proxies, 30+ with its anti-scraping protection, which can upgrade your proxy tier mid-request without you asking. On a $30 Discovery plan (200,000 credits) that 30-credit request means 6,667 pages at roughly $4.50/1K. On the $250 Startup plan (2.5M credits) the same request lands near $3.00/1K. Its headline $0.10/1K only holds for plain pages.

Two quirks worth knowing before you budget:

Google SERPs are expensive on ScraperAPI at 25 credits, which is $2.49/1K on Business. Scrapfly's own published measurement puts a Google result page at an average of 2.03 credits across about 4,300 production requests, which is roughly $0.20/1K on its $100 Pro plan. If your workload is mostly search results, that gap is the whole decision. ScraperAPI's counter is that its Google endpoint returns parsed JSON at the same credit cost, where Scrapfly's Extraction API adds credits on top.

The third-party benchmark puts blended cost at $5.81 per 1,000 scrapes for ScraperAPI and $3.75 for Scrapfly. Divide those by the measured success rates and you get roughly $9.70 per 1,000 *usable* pages against $3.93. Whether failed requests were billed in that figure is disputed, and it's worth testing yourself (more on that in the FAQ).

## Success rates by target

Independent benchmark data, October 1 to November 1, 2026:

| Target | ScraperAPI | Scrapfly |
| --- | --- | --- |
| All-target average | 60.1% | 95.3% |
| amazon.com | 93.9% | 93.0% |
| booking.com | 46.9% | 93.0% |
| etsy.com | 96.4% | 99.8% |
| indeed.com | 41.0% | 97.2% |
| instagram.com | no data | 74.7% |
| linkedin.com | 89.5% | 94.0% |
| realtor.com | 36.8% | 98.2% |
| stockx.com | 37.1% | 99.3% |
| twitter.com | no data | 97.7% |
| walmart.com | 89.5% | 99.8% |
| zillow.com | 99.9% | 98.9% |

The 60.1% average is dragged down by four targets: Booking, Indeed, Realtor and StockX, all sitting between 36.8% and 46.9%. On Amazon, Zillow and Etsy the two are within a couple of points of each other, and ScraperAPI actually edges Zillow.

Average response time in the same run was 10.6s for ScraperAPI against 16.3s for Scrapfly. Other comparison write-ups using different methodology put ScraperAPI at 4.9–7.3s and Scrapfly at 8.3–12.8s. The absolute numbers disagree across sources; the direction does not. ScraperAPI is the faster of the two.

ScraperAPI's own marketing claims a 99.99% success rate, and 95%+ on LinkedIn, Amazon and Cloudflare-protected pages. Treat that as a vendor figure. It is not what the independent benchmark recorded, and the 44-point gap between the two on Booking should be the thing you test first if Booking is on your list.

## The feature differences that change a decision

| Capability | ScraperAPI | Scrapfly |
| --- | --- | --- |
| Structured data endpoints | 18 endpoints (Amazon, Google, Walmart, eBay, Redfin), fixed JSON schema | LLM-powered Extraction API, no fixed schemas |
| Custom JS evaluation / browser control | Not offered | Yes, up to 160s, Playwright or Puppeteer over stealth Chromium |
| Screenshots | Not offered | Yes, full page and elements, 60 credits each |
| No-code scheduled jobs | DataPipeline, up to 10,000 URLs per project, scheduler plus webhooks | Requires Zapier, Make or n8n |
| SDKs | Python, Node.js, PHP, Java, Ruby, cURL | Python, TypeScript, Go, Rust, Scrapy |
| Compliance certifications | None publicly listed | SOC 2 Type II, ISO 27001, GDPR, HIPAA on custom plans |
| Session persistence | Persistent IP for 15 minutes | Persistent IP and cookies |
| Capterra | 4.6/5 from 62 reviews | 4.9/5 from 237 reviews |

The trade is clean. ScraperAPI returns finished JSON for the five domains it supports, so you don't maintain a parser. Scrapfly gives you a browser you can drive, which is what you need for login flows, infinite scroll and anything that has to be clicked before the data appears. ScraperAPI has no answer to a screenshot request or a 160-second custom script.

On compliance, Scrapfly publishes SOC 2 Type II and ISO 27001 coverage on every plan. ScraperAPI doesn't list those certifications publicly, which matters if your procurement team asks.

## When Scrapfly is the better buy

Four situations where I'd pay Scrapfly's higher per-page credit cost without hesitating:

1. **Your target list includes Booking, Indeed, Realtor, StockX, Instagram or Twitter.** ScraperAPI's 36.8% on Realtor means roughly six of every ten requests this month return nothing usable. That's not a pricing problem you can solve by upgrading.
2. **You need browser control.** Custom JS evaluation, waiting on a specific element, taking a screenshot as evidence, or scripting a multi-step flow. ScraperAPI doesn't do any of it.
3. **Procurement needs paperwork.** SOC 2 Type II or ISO 27001 documentation on request, with HIPAA available on custom terms.
4. **You want global geotargeting below $300/month.** Scrapfly includes 190+ countries on every plan; on ScraperAPI you need Business at $299.

Its free tier is 1,000 credits with no expiry and no card, which is enough to run a real sample. It has no annual plans, so every month is a fresh commitment, and its credits also reset rather than roll over.

## Which plan fits your volume

**Under 200,000 credits a month:** Hobby at $49. You get 20 threads and US/EU geotargeting. Fine for a single-country project on a target that bills 1–5 credits a page. At 75 credits a page this plan buys 1,333 pages, so measure before you commit.

**200,000 to 1M credits:** Startup at $149 gives 1M credits and 50 threads, still US/EU only. This is the awkward tier: three times Hobby's price for ten times the credits, but no country-level targeting.

**1M to 5M credits:** Business at $299 is the first plan worth defaulting to. 3M credits, 100 threads, country-level geotargeting, unlimited analytics history. At standard-page rates that's $0.10 per 1,000 requests.

**Above 5M credits:** Scaling at $475 (5M credits, 200 threads) is the first tier with pay-as-you-go, so a spike doesn't force an upgrade to a plan you don't need next month.

👉 [Compare ScraperAPI's plans at the $49, $149 and $299 tiers](https://www.scraperapi.com/?fp_ref=coupons)

Five things to check before you enter a card:

- Run your own URLs through the 7-day trial and watch credits consumed per URL in the dashboard, not the marketing page. Set `max_cost` on each request so a single expensive target can't drain the balance.
- Confirm your geotargeting requirement. US/EU on Hobby and Startup only.
- Decide monthly versus annual. 10% off is real, but only worth locking in once your credit burn is predictable for two or three months.
- Assume zero rollover. Size the plan to your average month, not your peak.
- If you need overflow billing, price Scaling rather than Business. Pay-as-you-go isn't available lower down.

## FAQ

**Does ScraperAPI have a free trial?**
Yes. Seven days, 5,000 credits, no credit card required. That's enough to run a few thousand requests against your real targets and see both the success rate and the credit burn.

**Which one is faster?**
ScraperAPI, consistently across every source I checked. The October benchmark measured 10.6s average against 16.3s; other comparison write-ups put it at 4.9–7.3s against 8.3–12.8s. The absolute numbers vary by methodology, the ranking doesn't.

**Can I get country-level geotargeting on the cheap plans?**
No. ScraperAPI restricts Hobby and Startup to US and EU locations. Country-level targeting starts at Business, $299/month. Scrapfly includes global geotargeting on its $30 plan.

**Are failed or blocked requests billed?**
ScraperAPI's stated policy is that unsuccessful and cancelled requests are not charged. One third-party benchmark lists "often charges for blocked requests" as a con, so the field reports don't match the policy. Test it: run twenty URLs you know are protected, then compare the credit deduction against the number of successful responses.

**Do credits carry over?**
No, on either platform. Balances reset at renewal.

If your targets are Amazon, Walmart, eBay, Zillow or Google and you want JSON back without writing a parser, start with Business at $299 and drop to Startup only if your measured credit burn says you can. If Booking, Realtor, Indeed or StockX are on the list, no ScraperAPI plan fixes a 37% success rate, and you should route those domains elsewhere while keeping ScraperAPI for the e-commerce and SERP work it does well.

👉 [Start the 5,000-credit trial and run your own targets through it](https://www.scraperapi.com/?fp_ref=coupons)
