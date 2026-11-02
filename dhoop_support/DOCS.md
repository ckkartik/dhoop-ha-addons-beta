# Dhoop Support

Lets Dhoop Smart Living help with your Home Assistant, only when you allow it.

## For the owner

Open **Dhoop Support** in the sidebar.

- **Turn on Support** when you need help. Describe the problem if you can. Dhoop is notified and can see what this session sends.
- **Turn Support off** at any time.
- **Dhoop's access** decides what Dhoop can do while Support is off:
  - **Off**: no connection at all. Dhoop can only call or message you.
  - **Ask me**: Dhoop can send an access request to your approver phones, and knows this box is online. Nothing else.
  - **1, 7 or 15 days**, or **Always**: Dhoop can start a support session when needed, with a reason you'll see as a ticket. Timed access ends by itself and goes back to Off or Ask me. **End access now** ends it early.
- **Approver phones** get Dhoop's access requests: Allow, Deny, or Other options (opens this panel, where you can pick any length). The first answer wins and clears the request from the other phones. Add a phone here, then tap **Confirm** on the notification it gets. Without Nabu Casa, a tap reaches home only while the phone is on the home Wi-Fi.
- **Auto-support**: the watchdog checks this home every minute and keeps what it finds here. With Auto-support on, a real problem that lasts 15 minutes (such as an integration that failed, or several devices offline) turns Support on by itself, at most 3 times a day. With it off, the watchdog only tells you.
- **When Dhoop starts a session**: you're told every time, or in a weekly summary.
- **Updates**: Dhoop keeps add-ons, custom integrations, Home Assistant and the OS up to date, only while it has access and only inside the maintenance window you set here (1–5 AM by default). A full backup comes first and checks come after; anything that fails stops the update. With Access set to Always, a short weekly check runs too, and opens a session only if something needs a look.
- **AI assistant**: during a session, Dhoop's assistant looks into the problem and suggests fixes, which a Dhoop technician approves. It runs on this machine; what it reads is sent to the AI provider (DeepSeek's servers are in China), never cameras, people, locations, locks, alarms or anything from your phones. Door, motion and presence sensors show whether they work, not what they report. Dhoop's own key is used as part of your AMC, or you can paste your own key here (it stays on this machine, and your provider bills you).
- **What the assistant remembers**: standing instructions and facts about your home, saved only when a Dhoop technician confirms them, plus past tickets and messages, all on this machine. You can delete any saved item. Every night, inside the maintenance window, it's backed up into Home Assistant's backups as "Dhoop memory" and the date: this add-on alone, never raw data, to this machine and wherever your own backups go (not Home Assistant Cloud), with your backup encryption key. These backups are deleted after 60 days; no other backup is ever touched.
- **Forget everything** deletes everything Dhoop Support has learned about your home: tickets and messages, what the assistant remembers, fixes, the activity log, raw data and the Dhoop memory backups. Dhoop's server deletes its ticket summaries for your home and your home's Telegram topic. The panel asks you to confirm first, and then lists what was deleted and anything that couldn't be. Your settings and the pairing stay. Your own full Home Assistant backups may still hold older copies of this add-on's data.
- **Activity** lists everything that happened: who turned Support on or off, which fixes Dhoop proposed and who approved them, and when Dhoop had the Home Assistant screens open.
- **Is it working now?** When Dhoop marks your problem fixed, the panel asks. Answer yes to close the ticket (Support turns off), or no to keep it open. If you don't answer, it closes after 48 hours.
- When a session ends, a report appears in Home Assistant's notifications.

You can also flip Support with the `input_boolean.dhoop_support` entity, for example from a dashboard card or a button.

**If the Mini PC dies:** install Home Assistant and Dhoop Support on the new one, then restore just Dhoop Support from the newest "Dhoop memory" backup (Settings → System → Backups). The memory, tickets and settings come back, including the pairing.

## For the Dhoop technician (setup)

1. Create the `dhoop` user in HA: an administrator, with **Can only log in from the local network** on.
2. Log in as `dhoop`, create a long-lived token (Profile → Security), and paste it into this panel.
3. Press **Pair with Dhoop** and enter the 6-digit code on the Dhoop dashboard (Pair a site).
4. Turn Support on, check that the ticket reaches the site's Telegram topic, then turn it off.

When signed in as `dhoop` through **Open HA**, this panel shows a technician view with the fixes waiting for approval, and the things the assistant offered to remember (Save, Skip, Delete). Set Dhoop's site key for this home under **AI assistant** (not possible if the owner uses their own). High-risk fixes can only be approved here. Access, approver phones and Auto-support are shown read-only: only the owner can change them. Turning Support on as `dhoop` is ignored; Dhoop starts sessions from the dashboard or Telegram, with a reason, while the owner has given access.

## Options

- `relay_url`: the Dhoop server's address. Leave it as installed.
- `read_only`: on by default. While it's on, this add-on only reads Home Assistant: it creates no Support toggle, sends no notifications, and fixes, updates and the Open HA tunnel don't run. Dhoop turns it off when the home is ready.
