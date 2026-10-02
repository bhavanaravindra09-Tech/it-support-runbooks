# VPN Won't Connect

**Applies to:** Remote users on the corporate VPN client (e.g. GlobalProtect / AnyConnect / Windows built-in).

## Symptoms
- VPN client errors out, hangs on "connecting", or connects then drops.
- "Authentication failed" or "gateway not reachable".
- Connected to VPN but can't reach internal sites/drives.

## Quick checks
1. Is their **home internet** working? (Can they load an external site?)
2. Are they on the **latest VPN client version**? (Outdated clients are a top cause.)
3. Did their **password expire** recently? VPN auth fails silently on expired passwords.
4. Are they on public/hotel Wi-Fi with a captive portal? They must accept the
   portal page *before* starting VPN.

## Step-by-step fix
1. Confirm internet works (browse to an external site).
2. If on captive-portal Wi-Fi: open a browser, accept the portal, then retry VPN.
3. Check credentials: have them sign in to webmail/portal — if that fails,
   treat as a password issue first (see `account-unlock-password-reset.md`).
4. Update or reinstall the VPN client from the official download link.
5. In the client: verify the **gateway/server address** matches the documented one
   (users sometimes have a stale entry).
6. If connected but no internal access: run `ipconfig /flushdns`, then retry.
   Check whether the issue is DNS (names fail, IPs work) vs routing.
7. As a workaround: try a different network (phone hotspot) to isolate
   ISP-level blocking.
8. Log: error message verbatim, client version, network type, time.

## Escalation criteria
- Multiple users failing simultaneously → likely gateway/firewall issue; escalate to network team immediately.
- `Authentication failed` with confirmed-good credentials → possible MFA /
  RADIUS / certificate issue; escalate to L2 with the exact error and timestamp.
- Suspected compromised credentials (user reports they didn't attempt logins) →
  follow the security incident process, not just a VPN fix.
