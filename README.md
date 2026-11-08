# Windows virtual server hosting: how much of the monthly bill is the licence, how many people can log in at once, and when bare metal beats a VPS (SpinServers plans compared)

A Windows virtual server carries three separate costs: the virtual hardware, the Windows licence, and the Remote Desktop users past the two administrator sessions that ship with Windows Server. Most hosts advertise the first and let you discover the other two after you have migrated. SpinServers runs Windows on a bring-your-own-licence basis, so the Windows key never appears in the monthly price at all — which makes the sticker cheaper than it looks and puts the licence arithmetic on you.

That one design decision explains who should buy here and who should not. SpinServers is a bare-metal-first host in Dallas and San Jose, and its virtual line is a smaller side of the business. If you want reserved CPU and RAM, a 1 Gbps or 10 Gbps port, and you already hold Windows Server keys, the Advanced Application Servers at $31–$45 a month are the obvious entry. If you are running one small accounting package for two people, a $14 plan is enough and a dedicated box is money set on fire.

> **Quick pick:** the Advanced Application Server at 12 vCPU / 12 GB / 160 GB SSD with 10 TB on a 1 Gbps port, listed at $31/mo, covers most small-team Windows workloads — remote desktops, a light IIS site, a bot or a trading terminal that has to stay awake. 👉 [Check current SpinServers Windows-capable plan pricing](https://bit.ly/Spinservers)

## The plans, as currently listed

SpinServers sells its KVM virtual servers under two names, Simple Application Servers and Advanced Application Servers. Both run Linux or Windows, come with IPv4 and IPv6, use SSD in RAID10 and default to a 1 Gbps port. Provisioning is automated at roughly 30 minutes, and the control panel handles OS install, reinstall and reboot without a ticket.

| Plan | vCPU / RAM / SSD | Transfer and port | Price | Order |
| --- | --- | --- | --- | --- |
| Simple Application (20 GB) | 2 vCPU / 2 GB / 20 GB | 1 TB @ 1 Gbps, Dallas or San Jose | $14/mo | [Check this plan](https://bit.ly/Spinservers) |
| Simple Application (40 GB) | 2 vCPU / 2 GB / 40 GB | 4 TB @ 1 Gbps, San Jose | from $6/mo | [Check this plan](https://bit.ly/Spinservers) |
| Advanced 12 | 12 vCPU / 12 GB / 160 GB | 10 TB @ 1 Gbps | $31/mo | [Check this plan](https://bit.ly/Spinservers) |
| Advanced 16 | 16 vCPU / 16 GB / 320 GB | 15 TB @ 1 Gbps | $37/mo | [Check this plan](https://bit.ly/Spinservers) |
| Advanced 32 | 32 vCPU / 32 GB / 500 GB | 20 TB @ 1 Gbps | $45/mo | [Check this plan](https://bit.ly/Spinservers) |

Entry pricing moves with promotions and stock, which is why the two Simple configurations sit so far apart for similar hardware. Confirm the exact SKU and the renewal rate at checkout rather than relying on a comparison table, including this one.

The dedicated side is where the company's pricing gets interesting. These are single-tenant machines with IPMI or iKVM access, so you install Windows yourself from an ISO or an auto-install image, and you keep the whole box.

| Configuration | CPU | RAM / Storage | Network | Price |
| --- | --- | --- | --- | --- |
| E3-1280 v5 | 4 cores / 8 threads | 32 GB / 1 TB NVMe | 10 Gbps, 30 TB, Dallas | $49/mo |
| 2× E5-2630L v3 | 16 cores / 32 threads | 64 GB / 1.6 TB SSD | 1 Gbps unmetered, San Jose | $79/mo |
| 2× E5-2630L v3 | 16 cores / 32 threads | 256 GB / 2× 1.6 TB SSD | 10 Gbps, 30 TB, San Jose | $109/mo |
| 2× E5-2696 v3 | 36 cores | 128 GB / 480 GB SSD | 10 Gbps, 30 TB, Dallas | $149/mo |
| 2× Xeon Platinum 6162 | 48 cores / 96 threads | 1 TB / configurable | 10 Gbps, 100 TB, Dallas | $449/mo |
| 4× Xeon Platinum 8268 | 96 cores / 192 threads | 1.5 TB / 4× 3.84 TB NVMe | 10 Gbps, 100 TB, Dallas | $599/mo |

The San Jose facility is the one to look at if your users sit in Asia; the company positions it as an alternative to premium China-route dedicated servers, and keeps a 100 Mbps telecom-optimised configuration at $79/mo alongside the 10 Gbps builds.

## The licence is the part nobody quotes you

Windows Server on a SpinServers machine is BYOL. You supply the key, or you run an evaluation image until you have one. Either way the host is not selling you a Microsoft subscription, and that is unusual enough to matter when you compare monthly numbers with a provider that bundles the licence.

For scale, a host that does sell licences charges around $6.31 per vCPU. On a 1 vCPU box that single line can exceed the entire monthly server price. Microsoft's evaluation route gives you 180 days of full functionality, but it requires online activation within the first 10 days, and after day 180 the machine keeps your data and software while the host is entitled to shut it down every hour until a licence is applied. Adding the key later converts the installation in place, so no rebuild is needed.

Bringing your own licence also changes what you can legally run. Microsoft does not let hosting providers rent desktop Windows, so a Windows 11 Pro template installs unactivated and you type in your own product key after first login. Desktop editions allow a single interactive session, which rules them out for a team logging into the same machine.

👉 [See how the BYOL Windows servers are configured](https://bit.ly/Spinservers)

## How many people can work at once?

Windows Server includes two Remote Desktop sessions for administration. A third person logging in at the same time needs a Remote Desktop Services CAL, and those run about $8.90 per user per month. Five people sharing one server means three CALs, or roughly $320 a year on top of the hardware, with no end date.

That number reframes the plan choice. A 32 vCPU virtual server does not solve a concurrency problem; CALs do, and they cost the same whether the server is a $45 VPS or a $599 dedicated machine. If your team is three or more, put the budget into CALs first and pick hardware second. Above roughly four or five simultaneous users, the reserved cores of a dedicated box start earning their price, because a shared-vCPU VPS with five people hammering Excel macros will feel worse than its spec sheet suggests.

SpinServers' RDP access is standard on Windows images, with the administrator password mailed after provisioning. Where a firewall rule or a bad RDP setting locks you out, the dedicated servers have firewalled IPMI/iKVM access and the virtual machines can be reached through the panel console.

## Which Windows version should you install?

New deployments belong on Windows Server 2025, which is what hosts with current image libraries default to. Server 2016, 2019 and 2022 remain available at most providers for software that has not been certified on newer builds, and the feature differences are real but rarely decisive for a small office: 2025 adds hotpatching without reboots, Credential Guard and NVMe optimisation, while 2019 and 2016 exist mainly to keep legacy line-of-business applications running.

Two dates matter more than the feature list. Windows 10 reached end of support on 14 October 2025 and no longer receives security updates, so it should not appear in a new deployment. Windows Server 2008 and 2012 R2 are long past their own end-of-support dates as well.

SpinServers' own published Windows image list dates from 2021 and references Windows 10 along with Server 2008, 2012 R2, 2016 and 2019. A 2026 review of the service confirms Linux, Windows and ESXi auto-install options are still offered, but the specific Windows builds available today are worth confirming before you order. Ask which images are on the install list and whether the Windows template arrives as BYOL or as an evaluation build, since the two behave differently after 180 days.

## How SpinServers compares on the numbers people actually pay

| Provider | Windows entry price | Licence handling | Watch out for |
| --- | --- | --- | --- |
| MassiveGRID | $3.99/mo (1 GB Starter) | 180-day evaluation, or $6.31 per vCPU | Extra RDP users $8.90 each per month |
| Contabo | Cloud VPS 6 Windows Server $29.40/mo, 100 GB SSD, unlimited traffic | Windows Server preinstalled | 200 Mbit/s port on the small plan |
| Hostwinds | $14.94/mo for 1 CPU / 1 GB / 30 GB / 1 TB | Server 2012, 2016, 2019 images | No Microsoft SQL Server licences; backups $1/mo + $0.03/GB |
| IONOS | Not published on its Windows VPS page | Bundled with the plan | Cannot switch to Linux later without a new order |

Two things in that table are worth dwelling on. Contabo's Cloud VPS 6 lists 100 GB SSD and a 200 Mbit/s port at $29.40, which is a different shape of product from a 1 Gbps SpinServers VPS: more storage, less pipe. And IONOS locks the operating system at order time, so a Windows virtual server there is a one-way decision unless you buy again.

Backups deserve their own line. Hostwinds charges $1/mo plus $0.03/GB for nightly snapshots as an add-on, and SpinServers' virtual plans do not advertise an included backup service either. Budget for a backup method before you migrate anything you cannot rebuild.

Uptime claims across these providers range from 99.9% to 99.9999%, and they are marketing figures measured on different bases. None of them predicts what your particular machine will do.

## Who should not buy a SpinServers Windows server

If you need the licence bundled into the monthly price and do not want to deal with Microsoft at all, this is the wrong shop. If your workload is a single small site that would run happily on Linux, a Windows licence is pure overhead. If you want a managed Windows environment where someone else handles patches and monitoring, a self-managed bare-metal host is the wrong shape of product.

The month-to-month terms are also worth reading before you pay. A 2026 review notes that month-to-month services here generally carry no refund policy, which is normal for dedicated hardware but a sharp contrast to hosts that offer a trial window. Treat the first machine as a paid evaluation and size it modestly.

There is one more fit issue. The same reviewers who track this host's VPS line observe that its cores favour multi-threaded work over single-thread speed. A 32 vCPU plan at $45 is excellent value for parallel jobs, and a mediocre choice for a single-threaded desktop application that one person clicks through all day.

👉 [Compare the full Windows-capable line-up and current prices](https://bit.ly/Spinservers)

## Picking the right one

Two people, one Windows application, budget under $20 a month: take a 2 vCPU Simple Application Server at $14, bring a key you already own, and skip the dedicated range entirely.

A small team on remote desktops, a light IIS site, or a bot that must never sleep: the 12 vCPU Advanced plan at $31 carries the RAM headroom for Server 2025 plus a session or two, and 10 TB of transfer is more than a desktop workload will touch.

SQL Server, an IIS site under real load, five or more concurrent RDP users, or anything where a noisy neighbour would be visible: go dedicated, and start at the $79–$149 configurations rather than the $449 ones. The 256 GB San Jose machine at $109 is the value pick of that group if you need memory more than clock speed.

Two questions to settle before you pay. Which Windows images are on the current install list, and does the template arrive as BYOL or as an evaluation build with a 180-day clock? Then add up the true monthly figure: server, licence, CALs and backup storage. The plan price is only the first of the four.
