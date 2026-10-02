# Outlook Not Syncing

**Applies to:** Outlook desktop (Microsoft 365 / Exchange Online).

## Symptoms
- "Disconnected" or "Trying to connect…" in the status bar.
- New mail not arriving; sent mail stuck in Outbox.
- Folders not updating; search returns old results.

## Quick checks
1. Status bar: **Connected / Disconnected / Trying to connect**?
2. Is it **all of Outlook** or just one folder? (One folder → view/filter issue.)
3. Does **webmail (outlook.office.com)** work? If yes → local client issue.
   If no → account/mailbox issue.
4. Mailbox over quota? (Check webmail for a quota warning banner.)

## Step-by-step fix
1. **Work Offline toggle**: Send/Receive → Work Offline → wait 10s → toggle back.
   This alone resolves many transient sync stalls.
2. If still disconnected: close Outlook, reopen. Then check for Office updates
   (**File → Office Account → Update Options → Update Now**).
3. Rebuild the local cache for a corrupted OST:
   **File → Account Settings → Account Settings** → select account →
   **Change** → drag "Mail to keep offline" slider (e.g. 1 year), or delete
   the OST at `%LOCALAPPDATA%\Microsoft\Outlook\` and let it rebuild.
   (Warn the user: first sync after a rebuild can take a while.)
4. Disable suspect add-ins: **File → Options → Add-ins** → Manage COM Add-ins
   → uncheck non-Microsoft add-ins → restart Outlook.
5. Create a **new Outlook profile** as a last resort:
   Control Panel → Mail → Show Profiles → Add. (Old profile kept as backup.)
6. Log: Outlook version, mailbox size if known, which step fixed it.

## Escalation criteria
- Webmail also fails → mailbox/account issue; check licence assignment and
  account status in Microsoft 365 admin, escalate to L2 if healthy there.
- Multiple users affected → Exchange Online service health / network issue;
  check the M365 Service health dashboard and escalate.
- Send/receive errors with specific codes (0x8004010F, 0x800CCC0E…) persisting
  after profile rebuild → L2 with the exact code.
