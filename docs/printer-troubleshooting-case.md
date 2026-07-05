# Printer Is Not Printing

One of the most frequent support issues I handled involved printers that suddenly stopped working for no clear reason.

The conversation usually started with something like:

"It printed fine yesterday, but now nothing happens."

or

"The print job just disappears from the queue."

Before assuming a hardware failure, I found it useful to work through a few basic checks first.

## What I Usually Checked First

### 1. Check the Print Queue

The first step was always looking at the print queue itself.

Questions I asked:

- Is the job stuck at the top of the queue?
- Is the printer shown as offline?
- Are there old stuck jobs blocking new ones?

Clearing a stuck job and restarting the print spooler resolved many cases.

### 2. Verify the Printer Is Actually Reachable

Sometimes the printer looked idle but was not actually reachable on the network.

Common causes included:

- Printer sleep or power-save mode
- A loose or disconnected network cable
- The printer's IP address had changed

### 3. Confirm Driver and Default Printer Settings

Occasionally the issue was not the printer at all, but the workstation configuration.

Things I checked:

- Was the correct printer set as default?
- Was the driver still installed correctly?
- Had a recent update reset the printer settings?

## Lessons Learned

Most printer issues were not hardware failures. They were usually caused by:

- A stuck print queue
- A printer that lost network connectivity
- A workstation pointing to the wrong printer or driver

## Key Takeaway

When a printer stops working, check the queue first, then connectivity, then the workstation configuration. Most problems are solved without ever opening the printer itself.
