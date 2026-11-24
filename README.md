<div align="center">

<img width="100%" alt="TG Cleaner. Personal Telegram cleanup: find inactive chats, then leave, archive, or mute them." src="https://capsule-render.vercel.app/api?type=waving&color=0:6C2BD9,50:FF2E93,100:FFB703&height=220&section=header&text=TG%20Cleaner&fontSize=58&fontColor=ffffff&fontAlignY=32&animation=fadeIn&desc=Personal%20Telegram%20cleanup%20%C2%B7%20leave%2C%20archive%2C%20or%20mute&descAlignY=58&descAlign=50&descSize=18"/>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3200&pause=700&color=FFB703&center=true&vCenter=true&width=820&height=48&lines=Personal+Telegram+chat-list+cleanup;Groups%2C+channels%2C+and+bots;Leave%2C+archive%2C+or+mute+in+bulk;Chrome+extension+%2B+local+Python+service;Private+chats+and+Saved+Messages+stay+untouched" />
  <source media="(prefers-color-scheme: light)" srcset="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3200&pause=700&color=6C2BD9&center=true&vCenter=true&width=820&height=48&lines=Personal+Telegram+chat-list+cleanup;Groups%2C+channels%2C+and+bots;Leave%2C+archive%2C+or+mute+in+bulk;Chrome+extension+%2B+local+Python+service;Private+chats+and+Saved+Messages+stay+untouched" />
  <img width="820" alt="Personal Telegram chat-list cleanup. Groups, channels, and bots. Leave, archive, or mute in bulk. Chrome extension plus a local Python service. Private chats and Saved Messages stay untouched." src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3200&pause=700&color=6C2BD9&center=true&vCenter=true&width=820&height=48&lines=Personal+Telegram+chat-list+cleanup;Groups%2C+channels%2C+and+bots;Leave%2C+archive%2C+or+mute+in+bulk;Chrome+extension+%2B+local+Python+service;Private+chats+and+Saved+Messages+stay+untouched" />
</picture>

*Find dead groups, channels and bots, and busy chats you never actually read, then leave, remove, archive or mute the ones you pick. One confirmation. Your own account.*

<br/>

<img alt="Version 1.3.0" src="https://img.shields.io/badge/version-1.3.0-6C2BD9?style=for-the-badge"/>
<img alt="Python 3.10 or newer" src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img alt="Vanilla JavaScript" src="https://img.shields.io/badge/JavaScript-vanilla-F7DF1E?style=for-the-badge&logo=javascript&logoColor=1A1024"/>
<img alt="HTML" src="https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white"/>
<img alt="Chrome extension, Manifest V3" src="https://img.shields.io/badge/Chrome-Manifest_V3-6C2BD9?style=for-the-badge&logo=googlechrome&logoColor=white"/>

<br/>

<img alt="Telethon 1.45" src="https://img.shields.io/badge/Telethon-1.45.0-FF2E93?style=for-the-badge"/>
<img alt="aiohttp 3.14.5" src="https://img.shields.io/badge/aiohttp-3.14.5-FFB703?style=for-the-badge&logoColor=1A1024"/>
<img alt="Docker" src="https://img.shields.io/badge/Docker-ready-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
<img alt="Optional Railway deploy" src="https://img.shields.io/badge/Railway-optional-FF2E93?style=for-the-badge&logo=railway&logoColor=white"/>
<img alt="Personal use" src="https://img.shields.io/badge/personal_use-your_account-FFB703?style=for-the-badge"/>

<br/>

<a href="#overview">Overview</a> ·
<a href="#key-features">Features</a> ·
<a href="#tech-stack">Stack</a> ·
<a href="#how-it-works">How it works</a> ·
<a href="#getting-started">Getting started</a> ·
<a href="#deploy-on-railway">Railway</a> ·
<a href="#configuration">Configuration</a> ·
<a href="#usage">Usage</a> ·
<a href="#security">Security</a> ·
<a href="#troubleshooting">Troubleshooting</a>

</div>

## ✨ Overview

**TG Cleaner** is a personal-use cleanup tool for your Telegram chat list. It connects to **your own** Telegram account (phone number, login code, and an optional two-step password), lists your groups, channels and bots, and lets you act on the ones you choose.

By default it runs entirely on your computer. The Chrome extension is the dashboard. A small Python service on `127.0.0.1` holds the Telegram session. There is no hosted account and no analytics. You can optionally run that same service on [Railway](https://railway.com) or any Docker host. Read the warning in [Deploy on Railway](#deploy-on-railway) before you do: the session then lives on a server.

For each listed chat you see the type, @username or link, your role, unread count, muted and archived state, the last message in the chat, and **when you last read or posted there**.

**Private one-to-one chats and Saved Messages are never listed or touched.**

<div align="center">

<img src="docs/dashboard.png" width="100%" alt="TG Cleaner dashboard listing Telegram groups, channels and bots, with inactivity filters and bulk leave, archive and mute actions."/>

<sub>The dashboard. Same screen in the Chrome extension and, when you self-host, at the service URL.</sub>

</div>

## ⚡ Key features

| | |
| --- | --- |
| **Two meanings of inactive** | *No new messages in the chat* (dead groups, abandoned channels, unused bots) or *you haven't read or posted* (the chat may be busy; you never open it). Each uses 7 / 30 / 90 / 180 days, or a custom 1–3650. |
| **Three actions** | **Leave / remove** (leave groups and channels, delete bot chats, optionally block the bots), **Archive**, or **Mute** forever. |
| **Protection** | 🛡 **Protect** any chat. The service then refuses every action on it, and the list survives restarts. **Unprotect all** clears them after a confirmation. |
| **Safety guard** | On by default. *Select inactive* and *Select all shown* skip pinned chats, chats in your Telegram folders, and chats where you are admin or owner. |
| **Looks important** | Before a batch runs, the confirmation flags pinned chats, folder chats, admin chats, chats you posted in during the last 30 days, chats you read this week, and unread mentions. One click leaves them out, or protects them and leaves them out. |
| **Filters and selection** | Search, type buttons, role, public/private, pinned, folders, member count, posted / never posted, notifications, unread, mentions, protected. Sort, Select inactive, Select all shown, Deselect all, Shift+click ranges. |
| **Honest progress** | Every action shows the exact names first, asks once, then runs one item at a time. You see Telegram's real answer for each item and can retry the ones that can be retried. |
| **Out of reach, on purpose** | Private chats with people (including deleted accounts), **Saved Messages**, and old basic groups that were upgraded to supergroups. Owned groups and channels can be archived or muted here, not left. |

## 🧰 Tech stack

<div align="center">

<img alt="Python" src="https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img alt="Telethon" src="https://img.shields.io/badge/Telethon-1.45.0-FF2E93?style=for-the-badge"/>
<img alt="aiohttp" src="https://img.shields.io/badge/aiohttp-3.14.5-FFB703?style=for-the-badge"/>
<img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=1A1024"/>
<img alt="HTML" src="https://img.shields.io/badge/HTML-E34F26?style=for-the-badge&logo=html5&logoColor=white"/>
<img alt="CSS" src="https://img.shields.io/badge/CSS-1572B6?style=for-the-badge&logo=css3&logoColor=white"/>

<br/>

<img alt="Chrome Manifest V3" src="https://img.shields.io/badge/Chrome_Manifest_V3-6C2BD9?style=for-the-badge&logo=googlechrome&logoColor=white"/>
<img alt="Docker" src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
<img alt="Railway" src="https://img.shields.io/badge/Railway-0B0D0E?style=for-the-badge&logo=railway&logoColor=white"/>

</div>

| Layer | What it is |
| --- | --- |
| **Extension** | Manifest V3, plain HTML / CSS / JS. No build step, no frameworks. The only permission is `storage`. The toolbar icon opens the dashboard in a tab. The manifest `key` pins the extension ID to `fdjdkkclgclbgkhlhlfbnjkjocfjjijn`. |
| **Service** | Python 3.10+ ([Telethon](https://docs.telethon.dev) 1.45.0, aiohttp 3.14.5). Locally it binds to `127.0.0.1` only and keeps the session in `~/.tgcleaner/`. |
| **Hosted** | `Dockerfile` (Python 3.12) and `railway.json`. Cloud mode serves the same dashboard at `/` and reads settings from environment variables. |

Leaving groups needs Telegram's client API (MTProto) as a *user*. The Bot API cannot do it. The session stays in the service, so Telegram credentials never live in the extension or in Chrome storage.

## 🔀 How it works

```text
Chrome extension (dashboard tab)  ── HTTP, JSON ──▶  Local service (Python)  ── MTProto ──▶  Telegram
  UI only, no secrets                 127.0.0.1:8765    Telethon + aiohttp
  stores only UI preferences                            session in ~/.tgcleaner/
```

On Railway (or another Docker host) the same service listens on the platform port, serves the dashboard at its public URL, and stores the session on a volume mounted at `/data`.

The service never calls Telethon's `delete_dialog()`, because that helper deletes private conversations when given a user. Chats with people are filtered out when the list is built, so no action can reach them. Chat history is deleted only for bots, and only when you confirm.

<details>
<summary><b>Telegram methods used</b> (checked against Telethon 1.45, API layer 229)</summary>

<br/>

| Purpose | Telegram method |
| --- | --- |
| Send login code | `auth.sendCode` |
| Sign in / two-step verification | `auth.signIn`, then `account.getPassword` + `auth.checkPassword` (SRP; the password itself is never sent) |
| List groups, channels and bots | `messages.getDialogs` (all folders, including Archive) |
| Chat activity | date of each dialog's most recent message (comes with the list) |
| Your reading | unread count / read position from the list; if you're behind, `messages.getHistory(limit=1)` just below your read position gives the date of the newest message you've read |
| Your posting | `messages.search(from_id=you, limit=1)`: your newest message in that chat |
| Leave channel / supergroup | `channels.leaveChannel` |
| Leave basic group | `messages.deleteChatUser` with yourself as the user (your messages are **not** deleted) |
| Remove bot chat | `messages.deleteHistory(revoke=false)`: deletes your copy only; optional `contacts.block` |
| Archive | `folders.editPeerFolders` (folder 1 = Archive) |
| Mute | `account.updateNotifySettings` with "muted forever" |
| Disconnect | `auth.logOut`, then the local session file is deleted |

</details>

## 🚀 Getting started

### Requirements

- Python **3.10+** (`python3 --version`). On Windows, install from [python.org](https://www.python.org/downloads/) and tick **Add to PATH**.
- Google Chrome, or another Chromium browser that supports Manifest V3.
- A Telegram **API ID** and **API hash** for your own account (free; step 1 below).

### 1. Get your API ID and hash

1. Go to [my.telegram.org](https://my.telegram.org) and log in with your phone number.
2. Open **API development tools** and create an app (any title / short name; platform "Desktop").
3. Keep the page open. You need **App api_id** and **App api_hash**.

### 2. Start the local service

macOS / Linux, from this repository:

```sh
./start.sh
```

Windows: double-click `start.bat`, or run it from a terminal in this folder.

The first run:

- creates a virtual environment in `service/.venv` and installs `telethon` and `aiohttp`
- asks for your API ID and API hash (the hash is typed hidden)
- asks for the extension ID. Press Enter to accept the default. It is fixed by the manifest key.

These are saved to `~/.tgcleaner/config.json` (Windows: `C:\Users\<you>\.tgcleaner\config.json`) with owner-only permissions.

Leave the window open. You should see `TG Cleaner service on http://127.0.0.1:8765`. The same window also prints a dashboard URL: open `http://127.0.0.1:8765` in a browser, or use the extension in the next step. Keep the window open either way. Press Ctrl+C to stop.

Other commands, from the same scripts:

| Command | What it does |
| --- | --- |
| `./start.sh setup` / `start.bat setup` | Re-enter API ID, hash, and extension ID |
| `./start.sh --demo` / `start.bat --demo` | Fake data. Never contacts Telegram |
| `./start.sh logout` / `start.bat logout` | Log out of Telegram and delete the local session |
| `./start.sh reset` / `start.bat reset` | Delete the whole data folder, including API ID and hash. Type `yes` to confirm |

Point the script at a specific interpreter with `PYTHON=/path/to/python3 ./start.sh`.

### 3. Load the extension into Chrome

1. Open `chrome://extensions`.
2. Turn on **Developer mode** (top right).
3. Click **Load unpacked** and choose the `extension` folder in this repository.
4. Check the ID on the card is `fdjdkkclgclbgkhlhlfbnjkjocfjjijn`. The manifest `key` pins it, and the service only trusts that ID.
5. Optional: pin the extension (puzzle-piece icon, then pin).

### 4. Connect Telegram

1. Click the extension icon. The dashboard opens in a tab. (Or open `http://127.0.0.1:8765` while the service is running.)
2. Enter your phone number in international format (for example `+15551234567`), then **Send login code**.
3. Enter the code Telegram sends. It usually arrives in the Telegram app on your other device, not by SMS.
4. If two-step verification is on, enter that password.
5. The header shows **Connected as \<your name\>**. Your groups and channels load automatically.

Your phone number, code and password pass from the dashboard to the local service and on to Telegram. They are never written to disk or logged. Only Telethon's session file (`~/.tgcleaner/telegram.session`) is kept, so you stay logged in.

> Telegram treats this like any other login. You will see a "new login" message, and a session called **TG Cleaner (personal)** under *Settings → Devices*.

### Try it safely first (demo mode)

```sh
./start.sh --demo        # Windows: start.bat --demo
```

Demo mode uses **320 fake groups and channels plus 24 bots**, and never contacts Telegram. It accepts any phone number, code `12345` and password `demo`. Some leaves fail on purpose, and one simulated rate-limit pause shows how errors look. Stop it with Ctrl+C before starting the real service. Both use the same port.

## ☁️ Deploy on Railway

You can run the service on [Railway](https://railway.com) instead of your computer. **The dashboard is then simply your Railway link.** Open it in any browser, phone included. No extension and no terminal are required. The Chrome extension still works with a Railway deployment, via **Connection**.

> **Read this first.** On Railway, your logged-in Telegram session lives on a server on the internet. Without an access token, **anyone who finds the URL can use your Telegram account** through it while it runs. Setting `TGC_ACCESS_TOKEN` is optional but recommended. Either way, click **Disconnect** and delete the project when you are done.

1. **Create the service.** In Railway, *New Project → Deploy from GitHub repo* and pick this repository. Railway finds the `Dockerfile` and `railway.json` (health check on `/health`, one replica).
2. **Add a volume.** In the service, open *Settings → Volumes* (or right-click → *Attach volume*) and set the **mount path to `/data`**. Without it you have to log in again after every deploy.
3. **Set variables** (*Variables* tab). Names only. Put the real values in Railway, never in the repo.

   | Variable | What to put |
   | --- | --- |
   | `TG_API_ID` | Your API ID from my.telegram.org. Not needed when `TGC_DEMO=1`. |
   | `TG_API_HASH` | Your API hash. Not needed when `TGC_DEMO=1`. |
   | `TGC_ACCESS_TOKEN` | Optional. A long random secret, **24+ characters**. Generate one with `python3 -c "import secrets; print(secrets.token_urlsafe(32))"`. If set, enter the same value in the dashboard or the extension. |
   | `TGC_DEMO` | Optional. `1` runs fake data and does not contact Telegram. |
   | `TGC_LEAVE_DELAY` | Optional. Pause between leave / remove / archive / mute requests. |
   | `TGC_SCAN_DELAY` | Optional. Pause between chats during the activity scan. |
   | `TGC_EXTENSION_IDS` | Optional. Comma-separated extension IDs, if you changed the extension's key. |
   | `PORT` | Set by Railway. Other Docker hosts can set it. Cloud mode defaults to `8080` when it is unset. |
   | `TGC_DATA_DIR` | Set to `/data` by the image. Mount the volume there. |

4. **Expose it.** *Settings → Networking → Generate Domain*. You get a URL like `https://<something>.up.railway.app`.
5. **Open that link** and log in to Telegram. If you set `TGC_ACCESS_TOKEN`, the page asks for it first. It is kept in that browser only.

   *Using the extension instead?* Click **Connection**, enter the address (and the token, if set), then **Save & connect**.

Notes:

- Keep **one replica**. The running job and the login steps live in the service's memory.
- Logs are in Railway's *Deployments → Logs* (what the "service window" refers to elsewhere). Codes, passwords and tokens are never logged.
- Telegram will report a new login from Railway's server location. That login is this deployment.
- To go back to running it locally, set the address to `http://127.0.0.1:8765` with an empty token.
- The service starts in cloud mode with `python -m tgcleaner serve --cloud`. Any Docker host works the same way: run the image with the variables above, a volume at `/data`, and HTTPS in front of it.
- If `TGC_ACCESS_TOKEN` is unset, the process prints a warning at startup and anyone with the URL can use the service.

## ⚙️ Configuration

Local settings live in `~/.tgcleaner/config.json`. Change the port in that file and on the dashboard's "Start the local service" screen together.

| Key | Default | Meaning |
| --- | --- | --- |
| `api_id`, `api_hash` | (from setup) | From my.telegram.org |
| `port` | `8765` | Service port |
| `extension_ids` | `["fdjdkkclgclbgkhlhlfbnjkjocfjjijn"]` | Allowed extension IDs |
| `leave_delay_seconds` | `2.0` | Pause between leave / remove / archive / mute requests (minimum 0.5) |
| `scan_delay_seconds` | `1.0` | Pause between chats during the activity scan (minimum 0.3) |
| `max_auto_flood_wait` | `300` | Longest Telegram wait handled automatically, in seconds |

Set `TGC_DATA_DIR` to use a different data folder. On macOS and Linux the folder is `0700` and the files are `0600`.

Cloud mode does not read `config.json`. It reads the environment variables in the Railway table above. `TGC_LEAVE_DELAY` and `TGC_SCAN_DELAY`, when set, are applied with a floor of 0.3 seconds.

## 🎛️ Usage

### Finding what to clean

- **Inactive means**
  - **No new messages in the chat.** An item is inactive when its newest message is at least *N* days old. Use this for dead groups, abandoned channels and bots you no longer use.
  - **You haven't read or posted.** An item is inactive when you haven't read anything new or posted there for *N* days, *even if the chat itself is busy*. "Last read" is the date of the newest message you've read. It is close to when you last opened the chat.
- **Inactive for:** 7 / 30 / 90 / 180 days, or **Custom…** (1–3650 days).
- **Scan my activity** (needed for the second basis). The chat list already tells when you last read every chat you're caught up on, and whether the newest message is yours. For the rest, the scan asks Telegram, about 1–2 small read-only requests per chat, at roughly one chat per second. It changes nothing. Results are kept in `~/.tgcleaner/scan_cache.json`. Each chat's result is dropped automatically once you read further in that chat.
- **Unknown activity.** Telegram returned no messages (history cleared or hidden), or a chat isn't scanned yet. These items are counted separately and are **never** selected by *Select inactive*. Missing data is not treated as proof of inactivity.
- **The "You" column** shows when you last read (`read 5 months ago`) and posted (`posted 2 years ago`, `never posted`). `not scanned yet` means a scan would fill it in. Channels you can't post in show only reading.
- **Type buttons:** All · Channels · Groups (all kinds) · Supergroups (including broadcast groups) · Basic groups · Bots.
- **Filters.** Show: All / Inactive / Active / Unknown activity / Can't *action*. Under **More filters**: my role (member only / admin or owner), visibility (public @username / private), pinned, in my folders, members (under 100 … 10,000+), my messages (I've posted / I never posted; needs the scan), notifications (muted / not muted), protected (show / hide / only), has unread, mentions me. **Clear filters** resets them.
- **Sort:** least or most recently active (unknown always last), name, type, most unread.

### Protecting what matters

- **🛡 on each row** protects or unprotects a chat. **🛡 Protect selected** protects everything you've selected. **Unprotect all (N)** (shown while anything is protected) removes every protection after a confirmation. Find protected chats with *More filters → Protected → Only protected*. Protected chats get a green edge and can't be left, archived or muted until you unprotect them. The service enforces this, even for a job that's already running. The list is saved in `protected.json` next to the session.
- **Safety guard** (top right, on by default). *Select inactive* and *Select all shown* skip pinned chats, chats you added to one of your Telegram folders, and chats where you're an admin or owner. You can still click those one by one if you really mean it.
- **Looks important.** Before anything runs, the confirmation lists chats that are pinned, in a folder, where you're admin, where you posted in the last 30 days or read this week, or that have unread mentions, each with its reason. **Leave these out** removes them from the batch. **Protect them and leave them out** also protects them for next time.
- Folder detection uses the chats you explicitly added to your Telegram folders. Rule-based folder contents such as "all groups" are not counted.

### Acting on it

Pick the **Action** in the bottom bar:

| Action | What happens | You stay a member? |
| --- | --- | --- |
| **Leave / remove** | Leaves groups and channels. Deletes chats with bots (your side only). In the confirmation you can also **block** the selected bots so they can't message you again. | No |
| **Archive** | Moves chats to Telegram's Archive folder. Works for chats you own too. | Yes |
| **Mute** | Turns notifications off forever. | Yes |

- **Select inactive** selects the inactive items in the current view that the chosen action applies to. **Select all shown** selects every eligible item in the view. **Deselect all** clears everything. Click a row to toggle it. Shift+click selects a range. The counter shows how many selected items are hidden by the current filters. Switching the action deselects items it can't apply to.
- Clicking the action button asks the service to validate the selection. A dialog lists the exact names, and anything that will be skipped, with the reason. Nothing happens until you confirm.
- **Progress:** one item at a time, with a 2-second pause between them. Each row and the results list show *Left ✓*, *Deleted ✓*, *Archived ✓*, *Muted ✓*, *Not a member*, *Failed* (with Telegram's reason), *Rate limited* or *Not attempted*. You can close the tab. The job keeps running in the service, and reopening the dashboard shows it. Only one job (an action or a scan) runs at a time.
- **Retry N eligible** re-runs only the retryable failures (network problems, unexpected Telegram errors, rate-limited or cancelled items), again after a confirmation.
- **Reload list** fetches the list from Telegram again. Channels, supergroups and deleted bot chats disappear. Basic groups you left stay in Telegram's chat list (as in the official apps) and show as "You already left this group". Delete those in the Telegram app if you want them gone.

Suggested recipes:

| Goal | Setup | Then |
| --- | --- | --- |
| Dead chats | Inactive means "No new messages", 180 days | Select inactive → Leave / remove |
| Busy chats you never read | Inactive means "You haven't read or posted", 90 days | Scan my activity → Select inactive → Mute or Archive (or leave them) |
| Old bots | Type "Bots", 30 days | Select inactive → Leave / remove, tick "Also block" |

### What is never listed or touched

- Private one-to-one chats with people, including deleted accounts, and **Saved Messages**. They are counted in a note under the stats so you can see they were excluded.
- Old basic groups that were upgraded to supergroups. Telegram keeps a dead copy. The live supergroup is listed instead.

### Listed, but not left or removed here

Shown with the reason:

- Groups and channels **you own**. Transfer ownership or delete them in the Telegram app. You can still archive or mute them.
- Ones you already left, were removed or banned from, or that are no longer accessible.
- A channel's direct-messages inbox, and Telegram *Communities* or other new types this tool doesn't know.

### Rate limits

Telegram does not publish exact limits for leaving chats. The tool:

- sends one request at a time, with a 2 s pause between actions (`leave_delay_seconds` in `config.json`, minimum 0.5) and a 1 s pause between scanned chats (`scan_delay_seconds`, minimum 0.3)
- waits out a `FLOOD_WAIT` of up to 5 minutes (`max_auto_flood_wait`), with a countdown, then retries that item **once**
- stops the batch on a longer wait, or on a second wait for the same item. The remaining items are marked *Rate limited / not attempted*, and new batches of the same kind are refused until the wait is over. It never hammers Telegram with retries.

### Disconnect

Click **Disconnect** in the header. This calls Telegram's logout (ending the session) and deletes the local session file and the scan cache. If Telegram can't be reached, the local file is still deleted and you're told to end the session under *Settings → Devices* in Telegram.

From a terminal: `./start.sh logout` (Windows: `start.bat logout`). To delete everything, including your API ID and hash: `./start.sh reset` (Windows: `start.bat reset`).

## 🛡️ Security

These points describe the default local mode. In cloud mode the service listens on the platform's network and the Host check is dropped. If `TGC_ACCESS_TOKEN` is set, every request needs it (`Authorization: Bearer …`, compared in constant time). The API locks for a minute after 20 wrong tokens. If the token is not set, anyone with the URL can use the service. The extension refuses plain `http://` for anything but this computer.

- The service listens on **127.0.0.1** only, never on your network.
- Every `/api` request must:
  - come from `Origin: chrome-extension://fdjdkkclgclbgkhlhlfbnjkjocfjjijn` (or be same-origin, when you opened the dashboard from the service itself). Browsers don't let web pages fake the Origin header.
  - carry the `X-TGCleaner: 1` header. This forces a CORS preflight, which the service refuses for any other origin, so websites can't even trigger requests blindly.
  - address `127.0.0.1:<port>` or `localhost:<port>` in the Host header (blocks DNS-rebinding attacks). Dropped in cloud mode, which sits behind the platform proxy.
  - be JSON, under 64 KB, with strictly validated fields: numeric item IDs, at most 5000 per request, deduplicated.
- Actions are two-step. **Prepare** returns the validated names and a single-use token valid for 10 minutes. **Start** consumes the token. Reloading the list invalidates tokens. Only one job can run at a time. Items already left, archived or muted can't be submitted again for the same action. The scan is read-only and needs no token.
- Your API hash, Telegram session and scan cache (chat IDs with dates, no message content) stay in `~/.tgcleaner/` (folder `0700`, files `0600` on macOS/Linux). The extension stores the service address, the optional access token, and filter preferences in `chrome.storage.local`. The web dashboard stores the token in that browser's `localStorage`. The Telegram session is never stored in the browser.
- Login codes, passwords and request bodies are never logged. Group titles from Telegram are inserted as text, never as HTML.
- A program already running as your user could read the session file. That is true for every Telegram desktop client and is outside what a localhost check can protect against.

## 🧪 Tests

All tests are mocked. **None of them contacts Telegram or leaves anything.**

```sh
cd service
.venv/bin/python -m unittest discover -s tests -t .     # Windows: .venv\Scripts\python -m unittest discover -s tests -t .
cd ..
npm test                                                # or: node --test "tests/extension/*.test.mjs"  (Node 20+)
```

`npm test` has no install step. `package.json` only configures the JavaScript tests.

<details>
<summary><b>What each file covers</b></summary>

<br/>

- `service/tests/test_telethon_backend.py`: classification built from real Telethon TL objects (people's chats and Saved Messages excluded, bots included; owned, left, banned and unknown types not leavable; free read/post signals). Also checks that the exact requests are built for every action (`LeaveChannelRequest`, `DeleteChatUserRequest(chat_id, InputUserSelf)` without revoking history, `DeleteHistoryRequest(revoke=False)` repeated until done plus optional `BlockRequest`, `EditPeerFoldersRequest`, `UpdateNotifySettingsRequest`), and that private chats never reach Telegram. It covers the scan (`GetHistoryRequest` at the read position, `SearchRequest(from_id=self)`) with cache reuse and invalidation, maps every Telegram error, and tests login with 2FA (the code and password never appear in logs), logout and a stalled connection.
- `service/tests/test_jobs.py`: sequential pacing, partial failures, short and long flood waits, no hammering, cancel, crash safety, no double processing, scan jobs.
- `service/tests/test_server.py`: Origin, Host and header checks, CORS preflight, body limits, input validation, the login API, a 60-item bulk leave with mixed failures and a flood wait, retrying only eligible items, token reuse, archive/mute eligibility, bot removal with and without blocking, the scan endpoint, per-kind rate limits, and one job at a time.
- `tests/extension/logic.test.mjs`: filtering, sorting, thresholds, both inactivity bases, unknown-activity handling, eligibility per action, and the Select inactive / retry rules.
- `tests/extension/safety.test.mjs`: type and extra filters, protected chats never being eligible, the safety guard (pinned, folder and admin chats stay out of bulk selection), and the "looks important" reasons.
- `tests/extension/api.test.mjs`: the service address must be local `http` or any `https`. Plain `http` to a remote host is refused, so an access token is not sent in clear text.

</details>

## 🔧 Troubleshooting

<details>
<summary><b>Symptom → fix</b></summary>

<br/>

| Symptom | Fix |
| --- | --- |
| Dashboard says **Local service offline** | Start `./start.sh` / `start.bat` and keep the window open. If you changed the port, enter it on that screen. Check `http://127.0.0.1:8765/health` in a browser tab: it should show `{"ok": true, "app": "tgcleaner"}`. |
| **Service rejected this extension** | The extension ID differs from the configured one, usually because the `key` was removed from `manifest.json`. Run `./start.sh setup` and enter the ID shown on the dashboard (or on `chrome://extensions`), then restart the service. |
| **Access token missing or wrong** (hosted) | Click **Connection** and paste exactly the `TGC_ACCESS_TOKEN` value from Railway's *Variables*. After 20 wrong attempts the API locks for a minute. |
| Railway deploy fails / keeps restarting | Check *Deployments → Logs*. `Cannot start: …` names the missing variable. |
| Logged out after every Railway deploy | Add a volume mounted at `/data` (step 2 of the Railway section). |
| Connected, but the list stays empty / "Couldn't load your chats" | The dashboard shows the reason; the service window has the full details. Click **Try again**. If Telegram asked to wait, wait that long first. Chats that can't be read are skipped and counted under the stats instead of breaking the list. If it keeps failing, copy the error from the service window. |
| `Address already in use` on start | Another copy (or demo mode) is running. Close it, or set a different `port` in `config.json` and on the dashboard. |
| `python3: command not found` / wrong version | Install Python 3.10+. On macOS, `brew install python`. On Windows, install from python.org. You can point the script at a specific interpreter: `PYTHON=/path/to/python3 ./start.sh`. |
| "Telegram rejected the API ID / hash" | Run `./start.sh setup` again and copy both values exactly from my.telegram.org. |
| No login code arrives | It usually goes to the Telegram app on another device, not SMS. Wait a minute. Requesting codes repeatedly triggers a long wait. |
| "Telegram requires a login email" | Newer accounts may need a login email. Set it up in the official app, then try again. |
| "Too many attempts / wait N seconds" | Telegram's flood protection. Wait the stated time. Don't retry in a loop. |
| A leave shows **Rate limited** | Telegram asked for a long pause. Retry those items after the time shown. Consider raising `leave_delay_seconds`. |
| A leave shows **Failed: Connection problem** | The request may or may not have reached Telegram. Use **Retry**. If it had worked, Telegram answers "not a member", which is shown as such. |
| An item shows **Unknown activity** | With "No new messages": Telegram returned no messages for it (history cleared or hidden). With "You haven't read or posted": run **Scan my activity**. If it's still unknown, there is no record of you reading or posting there. Open it in Telegram to judge. The tool won't assume it's inactive. |
| The scan seems slow | It deliberately goes about one chat per second to stay clear of Telegram's limits. It is remembered, so only chats you've read since need scanning again. |
| An archived chat came back to the main list | Telegram un-archives chats that aren't muted when a new message arrives. Mute them as well. |
| Lost track of a session | In Telegram, *Settings → Devices*, terminate "TG Cleaner (personal)". Then delete `~/.tgcleaner/telegram.session` or run `./start.sh logout`. |

</details>

## 📁 Project structure

```text
extension/                 Chrome MV3 extension (no build step)
  manifest.json            pinned key → stable ID; only the "storage" permission
  background.js            opens and focuses the dashboard tab
  dashboard.html / .css / .js
  api.js                   talks to the service (127.0.0.1 by default)
  logic.js                 pure filter / sort / selection logic (unit tested)
  icons/                   toolbar and dashboard icons
service/
  tgcleaner/
    __main__.py            CLI: setup | serve [--demo | --cloud] | logout | reset
    config.py              private data dir, config validation, cloud env vars
    telegram_backend.py    Telethon: login, dialogs, classification, actions, scan
    jobs.py                sequential batch jobs (actions + scan) with flood-wait handling
    protect.py             your protected chats (saved list)
    server.py              aiohttp API, security checks, and the dashboard files
    models.py              shared data shapes
    fake_backend.py        demo mode / tests (no Telegram)
  tests/                   Python unit tests (mocked; no Telegram)
  requirements.txt         telethon, aiohttp
  requirements-dev.txt     pulls in requirements.txt; tests use unittest
start.sh / start.bat       create the venv, install, set up, run (local)
Dockerfile, railway.json   hosted deployment (cloud mode; dashboard at "/")
docs/dashboard.png         screenshot used above
tests/extension/           JS unit tests (Node 20+)
```

This project is for personal use: one person, their own account, their own computer (or a deployment they control and then delete).

## 💜 Credits

Built by **[Shahriar Ahmed](https://github.com/fr-ost)**, Co-Founder & COO of **[Unique Labs](https://www.uniquelabs.org)**.

[GitHub](https://github.com/fr-ost) · [Unique Labs](https://www.uniquelabs.org) · [shahriarahmed.net](https://shahriarahmed.net)

<div align="center">

<img width="100%" alt="Footer wave in amber, pink and violet" src="https://capsule-render.vercel.app/api?type=waving&color=0:FFB703,50:FF2E93,100:6C2BD9&height=110&section=footer"/>

</div>
