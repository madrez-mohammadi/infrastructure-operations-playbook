# DNS Resolution Is Failing While the Internet Still Seems "Up"

One issue I ran into fairly often in small office and school environments was a computer that could not open any websites, even though the network itself looked perfectly fine.

The conversation usually started with something like: "The internet is down again." Or sometimes: "I can't open any websites, but the little network icon says I'm connected."

At first this looked like a full outage, but in most cases it traced back to a DNS resolution problem rather than an actual loss of connectivity.

## What I Usually Checked First

### 1. Confirm It Was Actually DNS

The first step was separating a real connectivity outage from a name resolution failure.

Questions I asked:

- Can the machine ping a public IP address like 8.8.8.8 successfully?
- Does pinging a domain name like google.com fail with a "could not find host" error?
- Do other devices on the same network have the same problem, or just this one?

When the IP address pinged fine but the domain name did not, that pointed straight at DNS.

### 2. Check the Configured DNS Servers

Once DNS was the likely culprit, the next step was looking at which DNS servers the machine was actually using.

Common causes included:

- A manually configured DNS server that was no longer responding
- An old internal DNS server address left over from a previous setup
- A machine set to a static configuration while the rest used DHCP

Running ipconfig /all and checking the listed DNS servers usually revealed a stale or unreachable entry.

### 3. Flush the Cache and Test a Known-Good Resolver

When the settings looked correct, the problem was often a stale or poisoned local DNS cache.

Things I checked:

- Did running ipconfig /flushdns clear the issue?
- Did switching temporarily to a reliable public resolver like 8.8.8.8 restore name resolution?
- Did nslookup return an answer when pointed at a different DNS server?

If a known-good resolver worked while the configured one did not, that confirmed the original DNS server was the problem.

## Lessons Learned

Most DNS issues were not full outages and were usually caused by:

- A misconfigured or unreachable DNS server
- A stale local DNS cache holding an old or bad record
- A single machine left on a static DNS entry that no longer existed

Instead of assuming the whole network was down, testing an IP address against a domain name quickly separated a real outage from a DNS problem.

## Key Takeaway

When someone says "the internet is down" but the connection looks fine, check DNS early. Ping an IP address, then a domain name, verify the configured DNS servers, and flush the cache before assuming a larger outage. Most cases are resolved without touching the router or the internet connection at all.
