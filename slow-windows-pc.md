# Slow Windows PC

**Applies to:** Windows 10/11 desktops and laptops.

## Symptoms
- Everything is slow: boot, login, opening apps, switching windows.
- Fan loud / PC hot; disk light constantly on.

## Quick checks
1. **When did it start?** (Gradual over months vs sudden after an update/install.)
2. Open **Task Manager → Performance**: is CPU, Memory, or Disk pinned at ~100%?
   Note *which process* is consuming it.
3. How much **free disk space**? (Under ~10% free on C: causes major slowdowns.)
4. Is it slow **only on VPN / only in one app**? (Then it's network/app, not the PC.)

## Step-by-step fix
1. **Reboot** — seriously. Check uptime in Task Manager; PCs with 30+ day
   uptimes accumulate leaked memory and stuck updates.
2. If Disk is at 100%: run **Disk Cleanup** (`cleanmgr`), empty Recycle Bin,
   clear `%TEMP%`. Uninstall unused large apps (Settings → Apps).
3. If a single process hogs CPU/Memory: end it in Task Manager; if it's a
   known app (Teams, Chrome with 40 tabs), advise closing/reducing; if it's
   `Antimalware Service Executable` mid-scan, let the scan finish.
4. **Startup tab** in Task Manager → disable non-essential startup apps.
5. Check Windows Update: install pending updates, then reboot.
   (A PC stuck "downloading updates" for days will crawl.)
6. Run a quick malware scan (Windows Security → Virus & threat protection).
7. If the drive is a spinning HDD and the PC is 4+ years old: note it as a
   hardware candidate (SSD upgrade / refresh) — don't promise it, just log it.
8. Log: Task Manager readings before/after, free space, uptime, outcome.

## Escalation criteria
- Slowness persists after cleanup + updates with healthy resource readings →
  possible failing drive or deeper OS issue; L2 (check SMART / reimage).
- Suspected malware that Windows Security can't remove → security team,
  isolate the machine from the network.
- Company-wide slowness after a patch/update rollout → L2 / desktop
  engineering; don't reimage one-offs until the pattern is confirmed.
