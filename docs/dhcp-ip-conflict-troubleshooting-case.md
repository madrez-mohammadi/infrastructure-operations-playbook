# IP Address Conflict Is Breaking Network Connectivity

One recurring issue in small office and school environments was a device suddenly losing network access even though "nothing changed."

The conversation usually started with something like: "It worked fine this morning, now it just says limited connectivity." Or sometimes: "Two computers keep kicking each other off the network."

At first this looked random, but in most cases it traced back to duplicate or conflicting IP addresses on the network.

## What I Usually Checked First

### 1. Confirm the Conflict

The first step was checking whether Windows was actually reporting an address conflict.

Questions I asked:

- Does the system tray show a "limited connectivity" or "IP conflict" warning?
- Does ipconfig show a valid address, or a fallback 169.254.x.x address?
- Did the problem start right after another device joined the network?

A fallback address almost always pointed to a failed DHCP handshake or a conflict.

### 2. Check for Static IPs Overlapping the DHCP Range

Many conflicts came from a device that had been manually assigned a static IP that fell inside the router's active DHCP pool.

Common causes included:

- A printer or old server configured with a static address years earlier
- A technician assigning a temporary static IP that was never removed
- A second router or access point handing out its own DHCP leases

### 3. Review the DHCP Lease Table

When the conflict wasn't caused by a static device, the next step was checking the router or DHCP server's lease table for duplicate or stale entries.

Things I checked:

- Were two devices listed with the same IP address?
- Were there far more leases than expected devices?
- Was the DHCP scope too small for the number of devices on the network?

Releasing and renewing the lease, or shortening lease time to clear stale entries, resolved most of these cases.

## Lessons Learned

Most IP conflict issues were not random and were usually caused by:

- A static IP address overlapping the DHCP range
- A rogue or misconfigured second DHCP server
- Stale leases that were never released

## Key Takeaway

When a device suddenly loses connectivity without any obvious change, check for an IP conflict first. Confirm the conflict, look for static addresses inside the DHCP range, then review the lease table. Most cases are resolved without touching cables or hardware.
