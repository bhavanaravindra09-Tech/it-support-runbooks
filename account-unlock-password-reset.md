# Account Unlock / Password Reset

**Applies to:** Windows AD-joined machines, Microsoft 365 accounts.

## Symptoms
- "Your account has been locked out" at the Windows login screen.
- Repeated "incorrect password" after a password change.
- Locked out of Outlook / Teams / VPN after too many attempts.

## Quick checks
1. Confirm the username spelling (ask them to read it off the screen).
2. Check Caps Lock and keyboard layout (FR/EN layouts swap keys).
3. Ask: "Did you recently change your password on another device?" — a phone
   or tablet with the old password is the #1 cause of repeat lockouts.
4. Verify identity: full name + employee ID (or another agreed verifier)
   before resetting anything.

## Step-by-step fix
1. Open **Active Directory Users and Computers** → find the user.
2. If locked: right-click → **Unlock account**. (Or `Unlock-ADAccount -Identity <username>`.)
3. If password expired/forgotten: right-click → **Reset Password** →
   set a temporary password, tick **"User must change password at next logon"**.
   (Or `Set-ADAccountPassword -Identity <username> -Reset -NewPassword (ConvertTo-SecureString "TempPass123!" -AsPlainText -Force)`.)
4. Tell the user the temporary password over a verified channel — never plain email.
5. Have them sign in on their **primary** device first, then update the saved
   password on phone/tablet mail apps and Wi-Fi.
6. Log the ticket with: username, cause (if known), time unlocked.

## Escalation criteria
- Account locks again within minutes with no bad logins from the user →
  possible brute-force or a stuck service; escalate to L2 / security.
- The user is not found in AD, or the account shows **disabled** → verify
  HR status before re-enabling; do not enable leaver accounts.
- Repeated lockouts across many users at once → possible domain controller
  or replication issue; escalate immediately.
