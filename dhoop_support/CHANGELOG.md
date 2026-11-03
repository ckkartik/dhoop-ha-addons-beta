# Changelog

## 0.10.0

The assistant can now use OpenRouter, so Dhoop can change models without a new release.

- On Dhoop's key, the assistant can work through OpenRouter (USA), which passes what it reads only to the hosts your agreement names (Anthropic, OpenAI, Microsoft Azure, Amazon Bedrock, Google Vertex, DeepInfra, Fireworks), and never to one that keeps it. Only a new release of this add-on can change that list. The panel says which route your home uses.
- Dhoop can switch the model homes on its key use, fleet-wide, through its policy pack. If you use your own key, your choice stays.
- AI spending now uses OpenRouter's own figure for each call, at the price of the host that answered.
- If none of the allowed hosts serves a model at the moment, the assistant says so plainly.

## 0.9.0

Fleet-wide settings from Dhoop, always within this add-on's own limits, and more for Dhoop's technicians to see.

- **Fleet notes and a policy pack** from Dhoop: lessons about particular integrations for the assistant, and settings such as how patient the watchdog is, AI prices, extra words that keep a device's readings private, and switches to turn the assistant or the weekly check off everywhere. This add-on applies them only within limits written in its code: they can make it more careful, never less; they never send your home's data anywhere new; and they never change your settings. Dhoop's server sends every note to every home: the assistant here reads only those for integrations your home has, so Dhoop's server never learns which you have.
- **Two new pages in Dhoop's live console**, during a session and through the same privacy filter as the rest: automations that are off or broken and recent runs that failed (a private automation, about presence, locks or a person, is never named), and what the assistant works with here (saved instructions and facts, its model, the playbook version and this month's AI spending).
- **Risky releases of Dhoop Support** can now be held back from Auto update and installed by Dhoop instead, home by home, in your maintenance window and with a backup, only after Dhoop's own test home took them.

## 0.8.1

- Dhoop's dashboard now hears every change to your Access and Auto-support settings, and to the AI key. Before, a change that kept the connection as it was (for example from 1 day to Always, or Auto-support on or off) showed there only after the add-on reconnected.

## 0.8.0

Answer Dhoop's access requests from anywhere.

- Allow and Deny on an access request now work wherever the phone has internet, not only on the home Wi-Fi. Each button is a one-time link through Dhoop's server, which only passes your answer on: this add-on checks it, and each phone gets its own links, so a Deny can never be turned into an Allow. A page opens to say it's done.
- Confirming a new approver phone, and Other options, still need the home Wi-Fi (or Nabu Casa).

## 0.7.0

Your home's memory: backed up, and yours to delete.

- Every night, inside your maintenance window, Dhoop Support asks Home Assistant for a small backup of itself alone, named "Dhoop memory" and the date. It holds what the assistant remembers, tickets and the activity log, never raw data. It goes to this machine and to wherever your own backups go (not Home Assistant Cloud, which keeps only one backup), with your backup encryption key if you set one. Dhoop Support deletes its own memory backups after 60 days and never touches any other backup. If one fails, the watchdog says so.
- **Forget everything**, in the panel under what the assistant remembers, for the owner only: after you confirm, it deletes every ticket and message, what the assistant remembers, fixes, the activity log, raw data and the Dhoop memory backups, and asks Dhoop's server to delete its ticket summaries for your home and your home's Telegram topic. The panel then lists what was deleted and anything that couldn't be. Your settings and the pairing stay.
- If Dhoop revokes this home's pairing (for example for a replaced Mini PC), the add-on stops connecting, ends a session that's on, and the panel offers to pair again.
- Backups of add-ons alone no longer count as the home's backups in the watchdog's "no recent backup" check.

## 0.6.1

Two fixes for setting up the add-on.

- A Support toggle left on in Home Assistant, for example from an earlier install of this add-on, no longer starts a support session by itself. The add-on turns it off and notes it in the activity log. Support starts only when someone asks for it while the add-on is running.
- If Support was turned on before this home was paired, Dhoop now hears about that session as soon as pairing is done. Before, Dhoop saw a session with no ticket and couldn't offer anything in Telegram.

## 0.6.0

Keeping Dhoop Support itself up to date.

- Dhoop can ask this add-on to install its newest release at once (Update now), instead of waiting for Auto update. Only while Dhoop has access or a session is on, only what Dhoop's add-on store already publishes, and with a backup first. Home Assistant installs it, and the add-on tells Dhoop how it went.
- Upgrading the add-on's database is now all or nothing: if it fails, nothing changes, the panel says the add-on is paused, and a copy of the database from before the upgrade is kept.
- The add-on tells Dhoop which protocol version it speaks, so Dhoop's server knows what it understands.

## 0.5.0

Phase 5: keeping the home up to date.

- Dhoop updates add-ons, custom integrations (HACS), Home Assistant and the OS through fleet rollouts that an admin approves once, with 2FA. Only while Dhoop has access, and only inside your maintenance window (1–5 AM unless you set other hours under **Updates**).
- At each run: Dhoop's assistant reads the release notes for breaking changes that touch your home, a full backup is taken, then add-ons, custom integrations (with a restart), Home Assistant, a check that everything still works (integrations loaded, no new Repairs, no new errors in the log), and the OS last. Anything that fails stops it there and keeps the session on for a technician.
- The panel shows scheduled and recent updates.
- With Access set to Always, a weekly check looks at the watchdog's findings, backups and waiting updates. It opens a session only if something needs a look; with the weekly summary on, you get "all good this week" otherwise.
- This add-on, the Supervisor and device firmware are never part of a rollout.

## 0.4.0

Phase 4: the AI assistant.

- During a session, the assistant triages as soon as Support turns on, answers Dhoop's technicians in the site's topic, and proposes fixes from the catalog. A technician still approves every fix.
- It runs on this machine and reads Home Assistant with the same privacy filter as Dhoop's console: cameras, people, locations, locks and alarms are never sent to the AI provider.
- Memory, kept on this machine: standing instructions and facts about your home (saved only when a Dhoop technician confirms one), a short summary of every closed ticket, and every message. "What happened last time?" is answered from past tickets, naming them.
- AI key: Dhoop's key for this home, or your own (BYOK), set in the panel. The model is DeepSeek Flash by default. A monthly budget warns Dhoop at 80 % and pauses the assistant at 100 %; technicians keep working by hand.
- The panel shows what the assistant remembers, and you can delete any of it.
- What was sent to the AI provider is kept in `raw/` (never in backups) and deleted 30 days after the ticket closes.
- Dhoop's playbook (how Dhoop works at every site) now arrives from Dhoop's server while Dhoop has access or a session is on.

## 0.3.0

Phase 3: access, approver phones and the watchdog.

- **Access** in the panel: Off, Ask me, 1, 7 or 15 days, or Always. Off keeps no connection to Dhoop. Ask me keeps a doorbell that can only carry access requests. With access given, Dhoop can start a session, with a reason that becomes a ticket you can see. 1, 7 and 15 days end by themselves.
- **Approver phones**: Dhoop's access requests arrive on these phones as HA app notifications with Allow, Deny and Other options. The first answer wins and clears the request from the other phones. Taps are checked inside your HA: answers from the `dhoop` user, or from phones that aren't approver phones, are ignored.
- **Watchdog**: checks integrations, devices, add-ons, disk, restarts, batteries, repairs and backups every minute. Findings stay in your home. With **Auto-support** on, a critical problem that lasts 15 minutes (20 after a power cut) turns Support on, at most 3 times a day.
- The panel shows the watchdog's findings, and the `dhoop` user sees your settings read-only. Turning Support on as `dhoop` is ignored.
- You're told in HA (and on approver phones) when Support turns on, when Dhoop starts a session (each time or in a weekly summary), and when a new HA user appears during a Dhoop session.
- Turning Support off while Dhoop has access asks whether to end the access too.

## 0.2.0

Phase 2: fixing things remotely.

- Live console for Dhoop: health, integrations, devices, logs, add-ons, updates, backups, network checks and activity, read on request and never stored by Dhoop.
- Fixes from a fixed catalog (reload an integration, restart an add-on, run an automation, take a backup, restart HA, install an update, test a light or switch, reboot, restore). Each is proposed, approved by a technician, run once and checked. High-risk fixes can only be approved in this panel, through the tunnel.
- The Dhoop tunnel: when a technician clicks Open HA, frpc opens the HA screens to them, and only them, for up to 30 minutes without activity. It closes when Support turns off.
- Dhoop can mark a ticket fixed. You confirm in the panel ("Is it working now?"), or it closes by itself after 48 hours. Closing the ticket turns Support off.
- A session that's been quiet for 48 hours, or on for 7 days, turns itself off.
- When a session ends, you get a report in HA's notifications listing what was done, by whom, and when the HA screens were open.
- The database now upgrades itself in place, keeping everything already stored.

## 0.1.0

First development release (Phase 1).

- Dhoop Support panel in the HA sidebar: turn Support on with a description of the problem, or off.
- `input_boolean.dhoop_support` is created automatically, so Support can also be flipped from a dashboard card, a button or a voice command.
- Pairing with Dhoop using a 6-digit code.
- While Support is on, the add-on connects to Dhoop, opens a ticket and answers "status".
- Tickets, messages and an activity log are kept on this machine.
