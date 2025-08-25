# Help Desk Ticket Simulations

> Purpose: Demonstrate structured troubleshooting, clear documentation, and user-focused communication.

---

## Ticket 001 — Printer not connecting
**User report:** “Cannot print from PC; printer shows ‘offline’.”  
**Environment:** Windows 10, networked printer (static IP .50).  
**Triage:** Confirm network, check printer panel status, ping printer IP.  
**Investigation:**
- Printer panel shows connected to Wi-Fi.
- `ping 192.168.1.50` fails.
- Router table shows printer at `.150` (DHCP reassigned).
**Fix:** Update Windows printer port to `192.168.1.150`. Print test page OK.  
**Root cause:** DHCP lease changed; port pointed to old static.  
**Prevention:** Reserve printer IP in router (DHCP reservation) + add KB note.

---

## Ticket 002 — Wi-Fi connects, no internet
**User report:** “Wi-Fi says connected, but no websites load.”  
**Checks:** Other devices OK, so issue isolated to client.  
**Investigation:**
- `ipconfig /all` shows DNS 0.0.0.0
- `ipconfig /flushdns` + `ipconfig /renew` still no DNS
- Manually set DNS to 1.1.1.1 / 8.8.8.8
**Fix:** Internet access restored.  
**Root cause:** Corrupted DNS client settings.  
**Prevention:** Document manual DNS override steps; consider GPO for DNS.

---

## Ticket 003 — Account lockouts
**User report:** “Password correct but keeps locking.”  
**Investigation:**
- Lockout threshold reached repeatedly every 30 mins.
- AD logs show old credentials from user’s phone mail app.
**Fix:** Update saved password on phone and Outlook; unlock account.  
**Prevention:** Post-password-change checklist KB; MDM prompts for credential updates.
