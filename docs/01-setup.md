# 01 – Initial Setup: Reviving a MacBook Air with a Broken Screen

> ## Goal
> As I am getting closer to my graduation in May 2027, I want to implement what I've learned so far (and reinforce less known topics) into a cohesive project that can that I actually use and secure myself.
> The computer I will be using for this lab was the one I started my collegiate studies with at KU, but the screen eventually cracked after a staple (from a piece of paper) punctured the screen. Since then, this laptop has been sitting in my closet collecting dust; but why not give it a second life? It's the perfect way to learn more about security, logs, and threat detection before investing in devices with larger hardware specs.

## Laptop Starting Point
| Item | Details |
|---|---|
| Machine | MacBook Air 13" (M1, 2020) |
| Specs | 8GB RAM, 256GB SSD |
| Condition | Cracked internal display, battery showing "Service" and stuck at ~1% |
| OS | macOS Monterey (no longer receiving security updates) |

> ## Problem 1: Broken Display
> - Connected to my portable KYY second monitor over USB-C. It showed "C1" (signal detected) but stayed blank
> - Tested the monitor (it worked with my other laptop) and tried both ports
> - Found out the Mac was sitting idle at the login screen and not sending a video signal
> - Logged in blind: Confirmed laptop was awake by using Caps Lock light, typed my password, then the display came up (after using **Command + F1** to screen mirror).
> **Lesson: Check what the system is doing, not just the hardware.**
> The monitor showing "C1" meant the cable and port were working. The real problem was that the Mac was sitting at the login screen and wasn't sending video yet. Along the way I learned that USB-C ports and cables don't all carry the same things (some carry only power or data, not video), and that Command + F1 toggles screen mirroring. I could have given up when the screen stayed blank, but testing one possibility at a time is what got it working.

> ## Problem 2: Running the Laptop without a Screen
> - Turned on Remote Login (SSH) and Screen Sharing so I can manage it from my main Mac
> - Turned on "Prevent automatic sleeping on power adapter when the display is off"
> - Ran `sudo pmset -a disablesleep 1` so it keeps running with the lid closed

> ## Problem 3: Auto-Login After Reboots
> - Needed it to come back up on its own after a reboot or power loss
> - The option was greyed out because FileVault was on
> - Turned off FileVault, restarted, then auto-login became available
> - **Security tradeoff:** the disk is no longer encrypted, and anyone with physical access gets a logged-in session. I accepted this because the risk is mainly physical theft. The laptop stays at home, so I removed personal information from it to limit what a thief could access.
> - Removed Touch ID and Apple Pay from the device and signed out of iCloud to limit what's exposed

> [!WARNING]
> ## Problem 4: Failing Battery
> - macOS says "Service Recommended" and the battery won't charge
> - Risks: no backup power during an outage, and possible swelling
>> ### Mitigation:
>> - Current:
>>   - Check for swelling (none has happened since plugging it in a week ago)
>> - Possible Solutions:
>>   - Get a replacement from Apple (No Apple Care, will be expensive)
>>   - Get an Uninterruptible Power Supply (UPS)

> ## Security Decisions
> - Updated macOS from Monterey to 27.2.1 to get security patches
> - Turned on the macOS firewall
> - No port forwarding on my router. Remote access will go through Tailscale (next phase)

## What I Learned
- Limitations:
  - The 8GB of RAM and faulty battery limit what tools I will be able to use
- Unsupported software poses a security risk, as it may have unpatched vulnerabilities
- Risk Acceptance
  - I turned off FileVault which leaves the Mac unencrypted, but the use case of the hardware limits the vulnerability of that decision
- Work through / test one problem at a time
  - Use what you find to narrow down the possibilities of the problem

## Next Steps
- Install Tailscale and OrbStack
- Harden the system against a CIS benchmark
