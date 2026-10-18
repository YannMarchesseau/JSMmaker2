<img width="256" height="256" alt="icon_1024" src="https://github.com/user-attachments/assets/5b60bc1d-d771-41b0-961c-890a4a94eb59" />

# JSMmaker2

Visual configuration builder for Jamf Setup Manager.

JSMmaker2 is a native macOS application that lets you build, audit and validate Jamf Setup Manager configuration profiles visually, without editing XML by hand.

It connects to your Jamf Pro instance to pull policies, triggers, departments and buildings, generates the Setup Manager plist (or a Jamf School `.mobileconfig`), previews the result as Setup Manager will render it, and validates the whole configuration against the Setup Manager documentation.

JSMmaker2 2.4.9 covers every key documented for **Setup Manager 1.4.7** (ConfigurationProfile.md, Extras.md, Webhooks.md, Network.md).

---

# Requirements

- macOS 26 or later
- A Jamf Pro instance (user account or API client)
- Setup Manager 1.3 to 1.4.7 on the target Macs (the target version is selected at login)

---

# Features

- Jamf Pro authentication with login/password or OAuth API client
- Import existing Setup Manager `.plist` files and signed or unsigned `.mobileconfig` profiles, with **all** Setup Manager keys preserved
- Export a ready-to-upload plist, or a Jamf School `.mobileconfig`
- Automatic retrieval of policies, triggers, departments and buildings
- Automatic Self Service icon association when the linked policy has one
- External icon catalogs (global and per client)
- Setup Manager target selection (< 1.4, 1.4+, 1.4.3+, 1.4.7+) that gates the keys and languages written to the profile
- 21 Setup Manager localizations, filtered by target version
- Complete Setup Manager key coverage:
  - `title`, `message`, `icon`, `background`, `banner`, `accentColor`, `tileColor` (global and per action, light/dark)
  - `startingMessage`, `finishedMessage`, `finishedScript`, `finishedTrigger`, `finalAction`, `finalCountdown`
  - `computerNameTemplate`, `enrollmentUserID`, `userEntry` (default, placeholder, label, options, validation, localized values, `showForUserIDs`)
  - `hideActionLabels`, `hideDebugLabel`, `overrideSerialNumber`, `networkQualityCheck`, `totalDownloadBytes`, `actionOutputLogging`
  - `networkCheck` (localized labels), `webhooks` (classic, Slack, Teams, `DEBUG`)
  - Actions: `policy` (including the empty Recurring Check-in trigger), `installomator`, `shell`, `recon`, `watchPath`, `wait`, `waitForUserEntry`, with light/dark icons
- Live plist preview with syntax highlighting
- Setup Manager visual preview with light/dark simulation, per-language rendering, `hideActionLabels` and `##clear` tiles
- Comprehensive **Validate** report: errors, warnings and tips for every key
- Project files (`.jsmproj`) with autosave
- Local simulation of Setup Manager in debug mode
- Three interface styles (Cards, Classic, Liquid Glass)

---
# Menus Overview

## Connection
<img width="1339" height="955" alt="Capture d’écran 2026-10-18 à 16 09 44" src="https://github.com/user-attachments/assets/f70a41f8-28ef-4c54-9dee-6897b5cee3fb" />

The Connection menu allows you to connect JSMmaker2 to a Jamf Pro instance.
- Login/password authentication
- OAuth API Client authentication
- Setup Manager target version (defaults to the newest version, 1.4.7+; Settings can restore the last choice instead)
- Automatic retrieval of policies, triggers, buildings and departments
<img width="508" height="48" alt="retrieval" src="https://github.com/user-attachments/assets/e8f4c921-4a49-493a-a0cf-37d54d8f6448" />

---

## API Connection

Enable “Use API Client” to connect with an API client; otherwise JSMmaker2 expects a username and password.
<img width="531" height="380" alt="api" src="https://github.com/user-attachments/assets/7ced72dd-8cb4-4c30-ba6f-20f309b953dc" />


## API roles

TThe API Client needs at least:

- Read Computers
- Read Policies
- Read Departments
- Read Buildings
- Read Categories when using Jamf Extender (thanks to Larrystegall for the tip)

---

## Customization

All visual and functional Setup Manager options.

### Languages
<img width="1274" height="354" alt="Capture d’écran 2026-10-18 à 16 10 46" src="https://github.com/user-attachments/assets/7bd24ebd-3611-49c6-817c-2a3930c86342" />
- **Single-language mode**: texts are exported as plain strings and shown as typed on every Mac, whatever its system language. No language to pick.
- **Multi-language mode**: one value per language, exported as localized dictionaries; `en` is mandatory as fallback.
- 21 localizations: en, en-GB, da, nl, fi, fr, de, he, it, ja, ko, nb, pl, pt-BR, pt-PT, es, sv, tr, zh-Hans, zh-Hant, zh-TW. Languages added in Setup Manager 1.4.2 and 1.4.7 are only offered when the selected target supports them.
- Every per-language field shows a fixed-width language tag so the columns stay aligned.
- 
### Run Mode

- Enrollment (default)
- Login Window


### Visual Customization
<img width="1269" height="787" alt="VisualCustomization" src="https://github.com/user-attachments/assets/1c6d3ea8-242d-491d-ae49-d4f29c9c30f7" />

- Background image or color
- Accent color (hex or named system color such as `##gray`)
- App Icon
- Banner (image or color)
- Dedicated Light/Dark assets for each of them

### Messages
- Starting Message (1.4.3+)
- Finished Message (1.4+)
- Title and message with substitution tokens (`%model%`, `%serial%`…)
  
### Setup Manager options
- Hide action labels (`hideActionLabels`)
- Network quality check on/off (`networkQualityCheck`)
- Action output logging: always / error / never
- Estimated download size (`totalDownloadBytes`)
- Override serial number for screenshots (`overrideSerialNumber`)
- Hide the DEBUG label when DEBUG is enabled (`hideDebugLabel`)
<img width="1295" height="223" alt="Capture d’écran 2026-10-18 à 16 13 36" src="https://github.com/user-attachments/assets/fa2081fd-3183-462c-8a09-d70d08e6efc7" />
<img width="1295" height="223" alt="Capture d’écran 2026-10-18 à 16 13 36" src="https://github.com/user-attachments/assets/52e57332-19db-43a3-9ab6-c941bf4eb097" />
<img width="1296" height="445" alt="Capture d’écran 2026-10-18 à 16 12 21" src="https://github.com/user-attachments/assets/68e4a6e0-9789-4179-a70a-c6ca78c53ff8" />

### Additional Features

- Network verification with per-host, localizable labels
- Multi-language Help section (title, message and URL are all localizable) with QR code
<img width="1287" height="354" alt="Help" src="https://github.com/user-attachments/assets/ff574812-553a-4885-826e-0114aa5b6f2f" />
- Webhooks for the Started and Finished events: classic JSON, Slack or Microsoft Teams, with the optional `DEBUG` key (full URLs in the Setup Manager log)
<img width="1284" height="204" alt="webhook" src="https://github.com/user-attachments/assets/76464aa6-4ff6-4bfa-95fc-57d794dff80d" />

---
## User Entry

### Computer Name
<img width="1295" height="223" alt="Capture d’écran 2026-10-18 à 16 13 36" src="https://github.com/user-attachments/assets/42154833-eaca-487a-9100-a26a59299161" />

Three modes, independent from the rest of User Entry:

- **Not managed**: Setup Manager leaves the computer name alone.
- **Automatic (template)**: writes `computerNameTemplate`, for example `COMPANY-%serial%` or `Mac-%serial:=6%`. The Mac is renamed without any prompt. Device tokens are always available; user entry tokens (`%department%`, `%assetTag%`…) are only offered when the matching field is collected.
- **Ask the user**: enables the `computerName` field with an optional default value and placeholder.

### Fields

User Entry is disabled by default; the field list appears once it is enabled. All Setup Manager fields are supported:

- Default value and placeholder, each localizable
- Label override, localizable
- Options for Department, Building and Room
- Regex validation with localized messages
- `$EMAIL` shortcut for User ID
- `showForUserIDs` together with `enrollmentUserID = $EMAIL` to show the form to specific users only

Department and Building options are pre-filled from Jamf Pro only when the list is empty. Values imported from a profile are kept as-is so the profile can be audited; options that do not exist in your Jamf Pro console are flagged, with a one-click “Replace with Jamf Pro values” or “Add missing”.

---
## Actions

Build the Setup Manager workflow visually.
<img width="147" height="47" alt="AddAction" src="https://github.com/user-attachments/assets/a92352bc-7796-4839-b4ae-192a547b1d02" />

Actions can be reordered with arrows or drag and drop and customized individually. A label is mandatory for every action except Recon.

### Tile Color
- Global or per action, with an optional dark variant
- `##automatic`, `##background`, `##clear`, named system colors or hex values
- A per-action color always overrides the global one

### Time Zone Action
<img width="1300" height="217" alt="TimeZone" src="https://github.com/user-attachments/assets/febbe921-831e-47c6-b6b6-55da77a08069" />

A simplified Shell action listing all time zones, always placed first. Use a regular Shell Command action if you need it elsewhere.

### Available Action Types

#### Policy Trigger

- Uses the custom triggers retrieved from Jamf Pro
- Option “Recurring Check-in” to run the check-in policies (empty trigger)
- A missing or unknown trigger is never replaced automatically: it is shown as “Unknown trigger” in the list and reported as an error by Validate until you fix it
- Proposes the Self Service icon when available

#### Installomator

- Label validation against the official list
- “Check Label” button to search and filter labels
- Arguments list, `valuesfromarguments` mode
<img width="531" height="493" alt="CheckLabel" src="https://github.com/user-attachments/assets/41eae003-eff9-45f4-97b9-945d216f3d46" />

#### Shell Command

Absolute path, arguments list, `requiresRoot`.

#### Jamf Inventory Update (Recon)

Runs a Jamf recon at that position in the workflow.

#### Watch Path

Waits until a file or application exists (or disappears), with a timeout.

#### Wait

Pauses the workflow for a number of seconds.

#### Wait for User Entry

Visible only when User Entry is enabled. Setup Manager waits for the user to submit the form, sets the computer name and runs a recon, so following policies can be scoped on the entered data.

Every action can have a custom icon (catalog, URL, local path, SF Symbol) with an optional dark variant.

---

## Validate

The Validate button audits the whole project before export and lists errors, warnings and tips with the exact location. Among other checks:

- Unknown or missing triggers, Installomator labels, time zones
- Substitution tokens, color syntax, image sources, absolute paths, regular expressions
- Jamf Pro-only keys used in Jamf School mode, keys not supported by the selected Setup Manager target
- Languages not available for the target, missing translations
- `finalAction = none` without a finished script or trigger, `showForUserIDs` without `enrollmentUserID`, User Entry fields without default, placeholder or options
- Department and Building options not found in Jamf Pro, webhook URLs, network check hosts

A missing background image is reported as a warning, not an error.

---

## Preview

- **Plist Live Preview** panel with syntax highlighting, updated 350 ms after your last keystroke so typing stays fluid
- **Final Preview** window: Setup Manager rendering with a toolbar to switch language, simulate light or dark appearance, and close; honours `hideActionLabels`, tile colors and `##clear`
  <img width="1000" height="741" alt="Capture d’écran 2026-10-18 à 16 50 48" src="https://github.com/user-attachments/assets/d68816ff-b4f3-4173-959f-a0600120f5af" />


---

## Simulate

The Simulate button launches the real Setup Manager on your Mac with the current configuration, in `DEBUG` mode (no policy is run, nothing is installed) and without the red DEBUG label. It writes a temporary plist to your user preferences, removes the Setup Manager flag files, flushes the preferences cache and starts Setup Manager in your session. An administrator password is requested once.

> **Important: exclude your Mac from the managed Setup Manager profile before using Simulate.**
>
> Setup Manager always prefers a *managed* configuration (a configuration profile installed by Jamf Pro) over the local plist written by Simulate. If your test Mac receives the `com.jamf.setupmanager` profile from Jamf Pro, Simulate will show that profile instead of the project you are editing, or will not start at all.
>
> The recommended way is the one documented by Jamf in [Extras.md](https://github.com/jamf/Setup-Manager/blob/main/Docs/Extras.md): create an Extension Attribute named **Setup Manager Done** with this script, then a Smart Group **Setup Manager Done** with the criteria `"Setup Manager Done" is "done"`, and use that Smart Group as an **exclusion** (or scope limitation) of the Setup Manager configuration profile. Enrolled Macs that have already completed Setup Manager, including your admin workstation, then stop receiving the profile.
>
> ```sh
> if [ -f "/private/var/db/.JamfSetupEnrollmentDone" ]; then
>   echo "<result>done</result>"
> else
>   echo "<result>incomplete</result>"
> fi
> ```
>
> Alternatively, exclude your Mac from the profile scope manually. You can check with `sudo profiles show` that no `com.jamf.setupmanager` payload is present before simulating.

Setup Manager must be installed on the Mac (`/Applications/Utilities/Setup Manager.app`). To stop a simulation, click Continue in Setup Manager or press **Command + Control + Shift + E**.

The **Clean** button next to Simulate removes the Setup Manager flag file and the root preferences left by a previous run, and flushes the preferences cache. Use it when Setup Manager keeps showing an older configuration.

---

## Settings
<img width="1444" height="787" alt="Settings" src="https://github.com/user-attachments/assets/8608df72-e352-4ec2-8e51-d7c21f77c008" />

- Global icon catalog and per-client override, optionally merged
- Local image folder used as the starting point of Browse dialogs
- **Appearance**: Cards (default), Classic (standard macOS controls) or Liquid Glass
- **Setup Manager target at launch**: latest version or remember last choice
- Autosave every 1, 5 or 10 minutes
- Simulate reminder

---

# Useful Shortcuts

| Shortcut | Action |
|---|---|
| Command + Control + Shift + E | Quit a running Setup Manager (debug mode) |
| Command + O | Open Project |
| Command + I | Import plist |
| Command + M | Import mobileconfig |
| Command + E | Export plist |
| Command + S | Save project |
| Command + Shift + U | Check for updates |
| ← / → | Switch language in the Final Preview window |

---

# Download

Download the latest notarized package from:

https://github.com/YannMarchesseau/JSMmaker2/releases

---

# Credits

Developed by Yann Marchesseau  
WalkingBucket Studio  
Website: https://walkingbucket.fr  
LinkedIn: https://www.linkedin.com/in/yann-marchesseau-1b44b6119/

Setup Manager is developed by Jamf: https://github.com/jamf/Setup-Manager

# Special thanks to Appitel for authorizing the continuation and public release of this project.
<img width="300" height="90" alt="LogoAppitel" src="https://github.com/user-attachments/assets/613097e0-2505-4af6-b28b-68cbefc48794" />

Appitel is a Paris-based IT services company specialized in Apple device management and Jamf deployments.

Website: https://www.appitel.fr

LinkedIn: https://www.linkedin.com/company/appitel/
