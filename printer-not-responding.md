# Printer Not Responding

**Applies to:** Network printers on Windows 10/11.

## Symptoms
- Print jobs sit in the queue with "Error" status.
- Printer shows "Offline" in Windows despite being powered on.
- Nothing happens when printing; no error shown.

## Quick checks
1. Is the printer **powered on** and showing Ready (not an error code)?
2. Is it a **network** printer (queue says "Offline") or USB?
3. Can the user print a **test page from another PC**? (Isolates PC vs printer.)
4. Did anything change — new PC, moved desk, recent Windows update?

## Step-by-step fix
1. On the PC: **Settings → Bluetooth & devices → Printers** → open the print
   queue → **cancel all stuck jobs**.
2. Restart the **Print Spooler** service:
   `Win + R` → `services.msc` → Print Spooler → Restart.
   (Or admin PowerShell: `Restart-Service Spooler`.)
3. If still failing: remove the printer, then re-add it via
   **Add device** (network discovery) or the documented `\\printserver\printername` path.
4. Check the printer's **IP address** on its display panel; ping it from the PC
   (`ping <ip>`). No reply → network/cable issue, not a driver issue.
5. For driver errors after a Windows update: remove the printer, download the
   latest driver from the manufacturer's site, reinstall.
6. Log: printer name/queue, PC hostname, what fixed it.

## Escalation criteria
- Printer display shows a hardware error code (paper jam cleared but persists,
  fuser/maintenance-kit warnings) → facilities / hardware vendor.
- Printer unreachable by ping from multiple PCs → network team (switch port,
  DHCP reservation, VLAN).
- Print server queue backing up for many users → escalate to L2 / server team.
