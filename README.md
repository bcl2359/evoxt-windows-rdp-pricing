# Buy VPS Windows: Is $2.99/Month Enough, What Does the Windows Licence Really Cost, and Which Plan Fits 3–5 RDP Users? (Full Evoxt Plan Table)

A Windows VPS costs $2.99 to $15 a month at entry level, and $24 to $48 once you need 8 GB of RAM or more. The line that changes the total is Windows licensing. Some hosts bill it per vCPU on top of the plan price; others fold it into the sticker. Evoxt lists its Windows RDP plans from $2.99 at the same rates as its Linux VMs, with no separate licence line on the plan card.

Below are the full plan list, the per-vCPU licensing arithmetic that turns a $3.99 advert into a $12.62 surcharge, the point where shared cores stop being enough, and how Evoxt's numbers sit against four other providers.

> **Most people should start at VM-2: $11.99/month for 2 vCores, 4 GB RAM and 30 GB storage.** That covers one admin session running a line-of-business app, a small IIS site, or a bot that has to stay up. If 3–5 people need to be logged in at once, go to VM-8 ($47.99, 8 vCores, 16 GB) and budget RDS CALs separately. The $2.99 VM-0.5 is a Linux tier in practice.
> 👉 [Deploy a Windows RDP plan on Evoxt](https://bit.ly/EvoXt)

## Evoxt Windows RDP plans and prices

| Plan | vCPU / RAM / Storage | Monthly transfer | Price (USD/mo) | Order |
| --- | --- | --- | --- | --- |
| VM-0.5 | 1 vCore / 512 MB / 5 GB | 250 GB | $2.99 | [ Deploy VM-0.5](https://bit.ly/EvoXt) |
| VM-1 | 1 vCore / 2 GB / 20 GB | 500 GB | $5.99 | [ Deploy VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 vCores / 2 GB / 20 GB | — | $6.95 | [ Deploy VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 vCores / 4 GB / 30 GB | 1,000 GB | $11.99 | [ Deploy VM-2](https://bit.ly/EvoXt) |
| VM-4 | 4 vCores / 8 GB / 60 GB | 2,000 GB | $23.99 | [ Deploy VM-4](https://bit.ly/EvoXt) |
| VM-6 | 8 vCores / 8 GB / 60 GB | — | $29.99 | [ Deploy VM-6](https://bit.ly/EvoXt) |
| VM-8 | 8 vCores / 16 GB / 80 GB | 3,000 GB | $47.99 | [ Deploy VM-8](https://bit.ly/EvoXt) |
| VM-16 | 16 vCores / 32 GB / 100 GB | 5,000 GB | $95.99 | [ Deploy VM-16](https://bit.ly/EvoXt) |

All plans in USD, monthly billing. Every plan includes a weekly offsite backup at no extra cost, IPv4 and IPv6, a browser-based VNC console, a firewall you configure from the control panel, and API access. Deployment is automated and usually finishes in under five minutes.

Evoxt sells the same plan names across three network tiers (Standard, Premium, Premium Plus). Rates stay close across tiers while transfer allowances drop as you move up, and the $2.99 entry plan is listed at $3.49 on Premium Plus. A few plans that don't appear above, VM-0.75, VM-3 and VM-12, are offered on the Premium tier; check their specs and transfer on the deploy page rather than assuming a straight line between the rows.

## The $3.99 advert and the $10.30 invoice

MassiveGRID publishes the clearest breakdown of what a cheap Windows VPS actually costs, and the mechanism it describes is common across the budget end of the market. Every Windows Server template, 2016 through 2025, ships as Microsoft's **180-day evaluation** at no licence cost. You must activate it online within 10 days. After day 180 the VM **shuts down every hour** until a licence is attached.

To avoid that, you tick "Licence +$6.31/vCPU", which appears as its own line in the cart: **$12.62 a month on 2 vCPU, $50.48 on 8 vCPU**. Their $3.99 Starter is a single vCPU, so with the licence it is $10.30 a month for 1 vCPU, 1 GB RAM and 32 GB NVMe. At the top of that ladder the licence alone costs more than most budget hosts charge for an entire server.

Desktop Windows is a separate story. Windows 10 and 11 Pro templates come unactivated and you bring your own product key, because hosting providers cannot rent out desktop Windows licences. If a seller advertises a "Windows 10 RDP" box with admin rights, the key is either yours or the arrangement is not what the page implies.

Evoxt takes the other route. Its Windows RDP plans carry the same prices as its standard VMs, and the licence isn't itemised, which is the model Contabo uses with preinstalled Windows Server Standard and Atlantic.Net describes as licensed Windows Server editions included. Neither model is dishonest; they just mean the headline number is not comparable across providers until you know which one you're looking at.

## Shared cores or reserved cores: where a cheap Windows VPS stops working

MassiveGRID draws a usable line between the two. Shared vCPU is fine for a remote desktop, a small IIS site, bots and accounting software. Move to reserved cores when you run SQL Server, IIS under sustained load, three or more RDP users, or emulator and SEO farms that sit at 100% CPU for hours. On a shared plan, a neighbour's nightly backup or a compile job shows up on your side as slow queries, dropped requests and sessions that stall for no visible reason.

One correction worth making, because it affects how you read spec sheets: not every Windows VPS comes with dedicated CPU. Atlantic.Net's VPS page states that its servers have "pre-allocated… dedicated resources such as CPU, RAM, and storage that are not shared with other users." That page carries a March 2023 date and the claim doesn't survive contact with how shared-vCPU plans are priced elsewhere. Ask for the allocation model in writing before you migrate a database onto any budget plan.

Evoxt's plan cards list vCores without a shared-or-reserved flag. At $11.99 for 4 GB and $23.99 for 8 GB, those are shared-core economics, so size for bursty work: a desktop session, a web app, a build runner. If what you're moving is a SQL Server database under constant load, a reserved-core product starting around $18.84 a month at MassiveGRID is the honest comparison, not a cheaper shared plan.

## Two RDP sessions are included. The third is a Microsoft licence

Windows Server allows two concurrent administrative sessions out of the box. Anything beyond that needs the Remote Desktop Services role installed plus RDS CALs, which are bought from Microsoft or a reseller and cannot be bundled by the host. MassiveGRID prices the convenience at **$8.90 per extra user** on top of the plan.

So a five-person remote team needs two purchases: a VM with enough RAM to hold five interactive sessions (VM-8 at $47.99 with 16 GB is the realistic Evoxt starting point) and the CALs. If it's you plus one colleague, VM-2 at $11.99 covers it and CALs never enter the conversation.

The $2.99 plan deserves a blunt note: 512 MB does not carry a Windows desktop once a browser is open. Treat VM-0.5 as a Linux tier or a throwaway test box, and treat VM-1 at $5.99 with 2 GB as the real floor for a single Windows session.

## How Evoxt's pricing compares

| Provider | Entry Windows plan | What to check |
| --- | --- | --- |
| Evoxt | VM-0.5 at $2.99 (1 vCore / 512 MB / 5 GB) | Windows or Linux at the same rate, no licence line item |
| MassiveGRID | Windows VPS from $3.99 (1 vCPU / 1 GB / 32 GB) | 180-day evaluation; licence +$6.31/vCPU ($12.62 on 2 vCPU). Reserved-core Windows VPS from $18.84 |
| InterServer | 2 slices minimum: 1 core / 4 GB / 80 GB / 4 TB, Hyper-V, RDP preinstalled | 16 slices = $80/mo for 8 cores / 32 GB / 640 GB SSD; 8 slices and up include managed support |
| Atlantic.Net | Windows VPS from $15.00/mo | Licensed Windows Server editions included; page dated 2023, so treat the price as indicative |
| Contabo | Windows Server Cloud VPS, 4 vCPU / 8 GB / 100 GB | Advertised with a "first 24 months" figure the page renders ambiguously. Not usable as a monthly rate |
| IONOS | Windows VPS+ accessed over RDP | Price not published on the page reviewed; Windows VPS+ cannot be switched to another OS after ordering |

Where does that leave Evoxt? At $11.99 for 2 vCores, 4 GB and 30 GB with Windows included, it undercuts Atlantic.Net's $15 entry and lands below a 2-vCPU MassiveGRID build once the $12.62 licence is added. The trade-off is disk and transfer: InterServer's 16-slice plan gives 32 GB RAM and 640 GB SSD for $80, against Evoxt's 16 GB and 80 GB for $47.99. If your workload is RAM- and disk-hungry, InterServer's per-dollar math is better. If it's a small, fast box where a single-threaded app matters more than 600 GB of storage, Evoxt's is.

## Adding capacity without changing plans

Evoxt sells add-ons individually, which is useful when you're 1 GB short of comfortable rather than ready for the next tier: **$3/month per extra vCore, $2/GB/month for extra RAM, $3/month per additional IP**, and extra transfer at $3/TB on Standard, $12/TB on Premium and $24/TB on Premium Plus. Transfer beyond the allowance is throttled rather than billed, so a busy month slows you down instead of producing an overage invoice you didn't plan for.

That combination covers most growth cases without a migration. What it doesn't tell you is whether an in-place upgrade keeps your installed applications and RDP settings; other hosts handle this differently (InterServer, for instance, upgrades by adding slices and charging the difference), so ask support before you build a workflow around it.

## Before you pay

**Confirm the licence line.** Evoxt's plan cards don't show a Windows surcharge, which is the main reason its prices look low next to per-vCPU billing. Check the invoice total before you commit to annual billing.

**Confirm the renewal rate.** Discount codes circulate widely for this provider, including claims of recurring 40% off. Those claims trace back to coupon and affiliate pages rather than Evoxt's own pricing page, and they conflict with each other. Do the maths on the undiscounted rate first, then apply whatever the order form actually accepts.

**Match the plan to the job.** A single admin session with one app open: VM-1 at $5.99, or VM-2 at $11.99 if you want headroom for a browser and an Office suite. A small IIS or ASP.NET site with light traffic: VM-2. Three to five people logged in at once: VM-8 plus RDS CALs. SQL Server under sustained load, or an emulator farm: a reserved-core plan at another provider. Linux tinkering only: VM-0.5 at $2.99.

👉 [Check the current Evoxt Windows RDP plan list and start a deployment](https://bit.ly/EvoXt)
