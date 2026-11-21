#Roadmap

## Phase 1 – Initial setup
- [x] Get a working monitor for my Macbook
- [x] Set up remote access so the computer/server
- [x] Keep the server running with the lid closed
- [x] Make the server recover after a reboot or power loss
- [x] Remove personal info from the server
- [x] Update macOS
- [x] Turn on firewall
- [x] Create the GitHub repo and document

## Phase 2 – Remote access and containers
- [x] Connect over SSH and verify the server's host key fingerprint
- [x] Switch to key-only SSH and disable password login
- [x] Install Tailscale on the server, my M2 and my phone
- [x] Confirm SSH works over Tailscale from outside my home network
- [x] Install OrbStack and run a test container (Uptime Kuma)
- [x] Test that monitoring catches an outage
- [x] Write 02-remote-access.md

## Phase 3 – CIS hardening
- [x] Run baseline Nmap scans of the server over the LAN and Tailscale
- [x] Generate a CIS Level 1 baseline for macOS 27 with NIST's mSCP
- [x] Record the baseline audit score (27/96)
- [x] Reduce network exposure (stealth mode, firewall permissions, unneeded services)
- [x] Build and install a tailored configuration profile, excluding rules that conflict with the server
- [x] Harden sudo and enable audit logging
- [x] Close unneeded ports (Kerberos disabled, Uptime Kuma restricted to Tailscale)
- [x] Document accepted exceptions, false failures and a tool bug
- [x] Re-run the audit and Nmap scans for before/after results (84/96)
- [x] Write 03-cis-hardening.md

## Phase 4 – Vulnerability management
- [ ] Install Nessus Essentials
- [ ] Scan the server and devices I own
- [ ] Sort the findings by severity and track them in a table
- [ ] Fix them, rescan, and record what was resolved
- [ ] Write 04-vulnerability-management.md

## Phase 5 – Python automation
- [ ] Write a script that turns Nessus results or failed-login logs into a daily report
- [ ] Keep secrets in .env, never in the code
- [ ] Schedule it to run automatically
- [ ] Write 05-automation.md

## Phase 6 – Wazuh SIEM
- [ ] Deploy the Wazuh single-node stack (stop other containers first)
- [ ] Install Wazuh agents on both Macs
- [ ] Trigger test alerts (e.g., failed SSH logins) and confirm they're detected
- [ ] Write 06-wazuh-siem.md

## Phase 7 – Attack validation
- [ ] Set up a Kali VM in UTM on my M2
- [ ] Nmap scan the server before and after hardening, and compare
- [ ] Write 07-attack-validation.md

## Phase 8 – Identity
- [ ] Deploy Authentik with MFA in front of Uptime Kuma
- [ ] Write 08-identity.md

## Phase 9 – Finishing Touches
- [ ] Draw a network diagram
- [ ] Update the README status and resume bullets
- [ ] Apply to Garmin, and keep updating the repo after applying

## Ongoing
- [x] Check the battery for swelling every week
- [x] Install macOS updates promptly
- [x] Remove identifying info before every push
