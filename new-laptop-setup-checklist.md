# New-Laptop Setup Checklist

**Applies to:** Windows 10/11 laptops issued to new or existing staff.
Tick off each item; don't hand over the machine with unchecked boxes.

## Checklist

### Identity & access
- [ ] Joined to the domain / Entra ID (verify in Settings → Accounts)
- [ ] User can sign in with their own account (test login, not yours)
- [ ] Microsoft 365 apps activated under the user's licence
- [ ] VPN client installed, gateway configured, test connection

### Security baseline
- [ ] Windows fully updated (Settings → Windows Update → no pending)
- [ ] Endpoint protection / antivirus installed and definitions current
- [ ] Disk encryption enabled (BitLocker) — record recovery key in the
      documented safe location
- [ ] Screen lock set to 5 minutes; password meets policy

### Apps & data
- [ ] Standard app set installed (browser, PDF reader, Teams/Zoom, ticketing
      client) per the department list
- [ ] Printers mapped (office network printers)
- [ ] Shared drives / SharePoint shortcuts in place
- [ ] Old data migrated (if a replacement machine) — confirm with the user
      that their files are present before wiping the old device

### Handover
- [ ] Asset tag recorded: serial number, asset ID, assigned user, date
- [ ] User shown: how to connect VPN, where to get help (help-desk
      contact), password-change process
- [ ] Temporary passwords communicated securely (never plain email)
- [ ] Ticket updated with serial, asset tag, and setup completion time

## Escalation criteria
- Autopilot / domain join fails repeatedly → L2 (check device object,
  Autopilot profile, network).
- BitLocker won't enable (no TPM / TPM disabled in BIOS) → L2 or hardware
  vendor; do not ship an unencrypted laptop with company data.
- Licence shortage (M365 / app activation fails) → licensing admin before
  promising the user a timeline.
