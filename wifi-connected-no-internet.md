# Wi-Fi Connected but No Internet

**Applies to:** Windows 10/11 laptops on office or home Wi-Fi.

## Symptoms
- Wi-Fi shows "Connected" (or "Connected, no internet" / globe icon).
- Browser can't load pages; Teams/Outlook offline.
- Other devices on the same Wi-Fi work fine (or don't — note which).

## Quick checks
1. **Scope**: just this laptop, or every device on that Wi-Fi?
2. **Wired test** (office): does ethernet work? If yes → Wi-Fi-specific.
3. **Airplane mode / Wi-Fi toggle**: is Wi-Fi actually on? (Function key +
   Windows software switch both matter.)
4. Any **VPN** running? A stuck VPN tunnel blocks all traffic when it drops.

## Step-by-step fix
1. Disconnect from the Wi-Fi network and reconnect. If prompted, **forget the
   network** first, then rejoin with the correct password.
2. Run the built-in troubleshooter: **Settings → System → Troubleshoot →
   Other troubleshooters → Network and Internet → Run**.
3. Command-line reset (admin Command Prompt or PowerShell):
   ```
   ipconfig /release
   ipconfig /renew
   ipconfig /flushdns
   ```
   Then retry.
4. Full network stack reset (needs reboot after):
   ```
   netsh winsock reset
   netsh int ip reset
   ```
5. Check for a **static IP / custom DNS** left over from another site:
   adapter settings → IPv4 properties → should be "Obtain automatically"
   unless documented otherwise.
6. Update the Wi-Fi driver from the laptop manufacturer's support page
   (especially after a Windows feature update).
7. Log: network name, scope (one device vs all), which step fixed it.

## Escalation criteria
- All devices down on office Wi-Fi → access point / controller / ISP issue;
  escalate to network team, don't troubleshoot laptops one by one.
- `ipconfig` shows a 169.254.x.x address after renew → DHCP failure;
  if it affects multiple machines, escalate to network/DHCP admin.
- Suspected rogue access point or repeated de-auth attacks → security team.
