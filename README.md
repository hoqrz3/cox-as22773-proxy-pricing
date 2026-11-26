# Cox Communications proxy: what AS22773 IPs cost, why free lists break, and when a residential-IP VPS fits

Cox Communications proxies are IP addresses announced on AS22773, the autonomous system behind Cox's US cable broadband network. Providers that publish rates sell static ISP proxies on this ASN from roughly $1 per IP per month, and rotating residential traffic from about $3.50 per gigabyte. Those are market benchmarks from named sellers, not a quote from sixtynet.net.

sixtynet.net sells a different product. Its residential line is a VPS with a residential IP attached, and the store path files it under an AT&T Mobility residential store rather than Cox. If what you need is a US residential address you control for long-running work, the VPS form factor is the relevant part. If a target specifically trusts Cox's AS22773 reputation, this isn't the product for that.

The rest of this covers what AS22773 is, why the free Cox proxy lists are mostly dead ends, how per-IP and per-GB pricing compare, and which sixtynet.net plan fits which job.

> **Quick pick:** For a US residential IP with root access and a flat monthly bill, sixtynet.net's Residential-STARTER is the cheapest entry at $25/month. All four residential tiers showed 0 available at the time of writing, so confirm stock before paying. 👉 [Check current Residential availability](https://sixtynet.net/aff.php?aff=39)

## sixtynet.net plans at a glance

The residential line is the one that matters for a US residential IP. Each tier bundles a residential IP with a VPS, and CPU, RAM, NVMe storage and monthly traffic scale together. Prices are monthly.

| Plan | CPU / RAM / Storage | Traffic | Price | Stock | Order |
| --- | --- | --- | --- | --- | --- |
| Residential-STARTER | 2 cores / 2GB / 40GB NVMe | 5TB | $25/mo | 0 available | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-MICRO | 4 cores / 4GB / 80GB NVMe | 10TB | $45/mo | 0 available | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-MEDIUM | 8 cores / 8GB / 160GB NVMe | 20TB | $85/mo | 0 available | [Order](https://sixtynet.net/aff.php?aff=39) |
| Residential-LARGE | 16 cores / 16GB / 320GB NVMe | 40TB | $165/mo | 0 available | [Order](https://sixtynet.net/aff.php?aff=39) |

Two limits sit outside the price. Ports 80 and 443 are closed on residential plans, which the site attributes to IP risk-control reasons, so these aren't web-hosting boxes. And all four tiers were out of stock at the time of writing, which makes the cart, not this table, the source of truth on availability. 👉 [Check whether the Residential tier you want is back in stock](https://sixtynet.net/aff.php?aff=39)

The same catalog lists non-residential lines that don't fit this topic but matter if you're sizing up the seller as a whole:

| Line | Entry price | Billing | Note |
| --- | --- | --- | --- |
| LAX DDoS-protected | $200/yr | Annual | Four tiers to $1,600/yr; standard ports open |
| China Unicom Premium (AS9929) | $2,500/yr | Annual | China-optimized routing |

A separate AS9929 residential-IP line is also listed at configuration level; its price isn't shown on the page, and its refund is credited to site balance only.

## What AS22773 actually is

Cox registers AS22773 with ARIN, and the ASN dates to 2001. The network announces 13,106,432 IPv4 addresses across 4,873 IPv4 prefixes and 1,456 IPv6 prefixes. It operates as a major transit provider with two upstream transit providers, 12 settlement-free peers and 489 downstream customer networks. Cox itself was founded in 1962 and is headquartered in Atlanta, Georgia, with coverage across multiple US states.

The number shows up on every sales page because sites don't only score an individual IP, they score the network announcing it. An address inside a long-established cable broadband ASN reads as ordinary home traffic. An address inside AWS or OVH reads as datacenter, even when the seller calls it residential. Providers lean on that distinction when they advertise "real ISP" IPs. Treat it as their description, not an independently verified guarantee, until you've tested it against your own target.

## Why free Cox proxy lists fail

spys.one listed 26 open proxies under AS22773 on 2026-11-14, the most recent check on that page. ditatompel's list for the same ASN was last checked 2026-10-07, about five weeks earlier. The uptime figures explain the gap between a list entry and a usable IP.

A Mikrotik HTTP proxy at 66.210.33.34:8080 showed 10–11% uptime and non-anonymous status on both lists. A second Mikrotik HTTP entry at 68.225.17.237:8080 sat at 11%. Some SOCKS5 entries look healthy by comparison: 184.182.240.211:4145 at 100%, 72.207.109.5:4145 at 99%, 24.249.199.4:4145 at 79%. That spread is the problem. You aren't drawing from a maintained pool, you're drawing from whatever a scanner found, and the low-uptime entries are usually misconfigured routers or Squid caches that vanish without warning.

The two lists also disagree on where several IPs sit. The same address can carry different city tags on spys.one and ditatompel, which makes the geolocation too unreliable to target a metro. For anything location-sensitive, a free list is the wrong tool.

## Per-IP and per-GB pricing don't convert

Cox proxy pricing comes in two shapes.

Per IP, per month is the static ISP model: one fixed address for the billing period. Roundproxies publishes static ISP proxies from $1.00/IP. A smaller seller's summary lists 5 IPs at $15/month and 100 IPs at $149/month, or $3.00 and $1.49 per IP respectively. Treat those as indicative, since that listing wasn't fully verified.

Per GB is the rotating residential model: you pay for traffic, the exit IP changes, and the rate is commonly around $3.50/GB from providers that publish it.

The number that gets abused in comparison tables is about $2.50/IP from datacenter proxy sellers. That's a datacenter address, not a residential or ISP address on a cable ASN. Putting it in the same column as a Cox static IP compares two different products. If a table shows both without labeling them, the cheap row is doing marketing work.

## Who the sixtynet.net residential VPS fits

The VPS form factor is the real difference. A proxy subscription hands you an endpoint; a residential VPS hands you a machine plus the IP. That suits scrapers and account workflows that need to run continuously from one address without negotiating a provider's session rules.

It fits you if:

- You need a US residential IP and root on the box.
- You want a flat monthly price rather than per-GB billing.
- Your work runs from one long-lived address, such as social account management, SEO rank checks or ad verification.
- You can live without ports 80 and 443.

It doesn't fit you if:

- A target specifically whitelists Cox's AS22773. sixtynet.net runs a different network.
- You need rotating IPs by volume. Per-GB residential traffic is the better shape.
- You need public web hosting. The closed ports rule it out.
- You need stock today. All four residential tiers showed zero availability at the time of writing.

Refund terms for the residential line aren't spelled out on the product page, and the adjacent AS9929 line refunds to site balance only, so confirm the refund window and payment methods at checkout before paying. That check determines whether you're running a trial or committing.

## How to decide

The right pick depends on which part of "Cox proxy" you actually need.

- **You need Cox's AS22773 specifically:** buy a static ISP proxy on that ASN from a provider that sells it. sixtynet.net is not that.
- **You need a US residential IP you control, with root and a fixed price:** start with Residential-STARTER at $25/month. Move up only when 5TB of traffic or 2GB of RAM becomes the bottleneck, not because a bigger tier looks more serious.
- **You need rotating residential traffic by volume:** per-GB pricing from a residential network fits better than a VPS.
- **You need to host a public site:** skip the residential line and look at the LAX DDoS plans.

Before you pay, confirm two things: whether the residential tier you want is actually in stock, and what the refund window is. Both change the math more than the spec sheet does. 👉 [See the current sixtynet.net Residential plans and stock](https://sixtynet.net/aff.php?aff=39)
