<img width="256" height="256" alt="JSMmaker2-1024" src="https://github.com/user-attachments/assets/bcffac1c-1291-41bb-9ad4-f90b9954700e" />

# JSMmaker2

Visual configuration builder for Jamf Setup Manager.

JSMmaker2 is a modern macOS application designed to visually build and validate Jamf Setup Manager configurations.

The application connects directly to a Jamf Pro instance and helps administrators generate Setup Manager plist configurations without manually editing XML files.

---

# Features

- Jamf Pro OAuth / API authentication
- Login/password or API Client authentication
- Import existing Setup Manager plist files
- Import signed or unsigned `.mobileconfig` profiles
- Automatic retrieval of:
  - Policies
  - Triggers
  - Buildings
  - Departments
- Automatic Self Service icon association when available in the linked policy
- External icon catalog support
- Support for the latest Setup Manager 1.4.3+ features:
  - Title color
  - Banner support
  - Starting Message
  - Finished Message
  - Finished Script
  - Finished Trigger
  - Network verification
  - Webhooks
- Live plist preview
- Approximate Setup Manager visual preview with:
  - Dark Mode simulation
  - Multi-language rendering
- Multi-language support (13 languages)
- Validation and troubleshooting tools
- Project autosave support
- Live preview in Setup manager (debug mode without debug label)

---

# Menus Overview

## Connection
<img width="1123" height="514" alt="Login" src="https://github.com/user-attachments/assets/e6960367-b13b-4245-b51e-2407331da8fe" />

The Connection menu allows you to connect JSMmaker2 to a Jamf Pro instance.

Features include:

- Login/password authentication
- OAuth API Client authentication
- Setup Manager target version selection
- Automatic retrieval of:
  - Policies
  - Triggers
  - Buildings
  - Departments
<img width="508" height="48" alt="retrieval" src="https://github.com/user-attachments/assets/e8f4c921-4a49-493a-a0cf-37d54d8f6448" />

## API Connection

To connect using the API, enable the “Use API Client” option.
Otherwise, JSMmaker2 will expect a traditional username and password login.
<img width="531" height="380" alt="api" src="https://github.com/user-attachments/assets/7ced72dd-8cb4-4c30-ba6f-20f309b953dc" />


## API roles

The API Client must have at least the following roles/privileges:
- Read Computers
- Read Policies
- Read Departments
- Read Buildings
---

## Customization

The Customization menu contains all visual and functional Setup Manager options.

### Languages
<img width="1269" height="159" alt="Languages" src="https://github.com/user-attachments/assets/ffeb1f39-0414-47d4-adf9-9548a3d6eb23" />

- Single-language mode
- Multi-language mode
- 13 supported languages

### Run Mode

- Enrollment mode
- Login Window mode

### Visual Customization
<img width="1269" height="787" alt="VisualCustomization" src="https://github.com/user-attachments/assets/1c6d3ea8-242d-491d-ae49-d4f29c9c30f7" />

- Background image
- Accent color
- App Icon
- Banner support
- Dedicated Light/Dark mode assets

### Messages
<img width="1282" height="133" alt="NetworkCheck" src="https://github.com/user-attachments/assets/ff15f807-0b45-4db4-a204-d187e5a10e90" />

- Starting Message
- Finished Message
- Multi-language interface text

### Additional Features
<img width="1282" height="133" alt="NetworkCheck" src="https://github.com/user-attachments/assets/9a03ab0f-465f-40c6-b88d-9b7e4f1d95d3" />
- Network verification
- Multi-language Help section
- QR Code help redirection
  <img width="1287" height="354" alt="Help" src="https://github.com/user-attachments/assets/ff574812-553a-4885-826e-0114aa5b6f2f" />

- Event-based webhooks:
  - Started
  - Finished
<img width="1284" height="204" alt="webhook" src="https://github.com/user-attachments/assets/76464aa6-4ff6-4bfa-95fc-57d794dff80d" />

---

## User Entry

Disabled by default.

All Setup Manager User Entry fields are supported.

### Features

- Mandatory labels
- Optional regex validation
- Localized validation messages
- Automatic Building and Department retrieval from Jamf
- Placeholder support
- Dropdown support
- Wait for User Entry integration
<img width="1292" height="838" alt="Capture d’écran 2026-05-24 à 23 47 15" src="https://github.com/user-attachments/assets/110425f4-0a62-41e6-9769-0292319e9c74" />

---

## Actions

The Actions menu allows you to build Setup Manager workflows visually.
<img width="147" height="47" alt="AddAction" src="https://github.com/user-attachments/assets/a92352bc-7796-4839-b4ae-192a547b1d02" />

Actions can be:

- Reordered using arrows
- Reordered via drag and drop
- Customized individually

A Label is mandatory for every action.

### Tile Color

Tile Color can be:
<img width="1300" height="131" alt="Capture d’écran 2026-05-24 à 23 48 53" src="https://github.com/user-attachments/assets/de8febbb-3881-427a-86a1-ba8ae9c8239b" />

- Global
- Per-action

If a global color is configured but an action defines its own color, the action color takes priority.

Supported modes:

- Automatic
- Background
- Custom color

### Time Zone Action
<img width="1300" height="217" alt="TimeZone" src="https://github.com/user-attachments/assets/febbe921-831e-47c6-b6b6-55da77a08069" />

The Time Zone action is a simplified Shell action including all supported time zones.

If you do not want the Time Zone action to appear first, it is recommended to use a regular Shell Command action instead.

### Available Action Types

#### Policy Trigger

- Uses triggers retrieved from Jamf
- Automatically proposes the Self Service icon if available

#### Installomator

- Installomator label support
- Label validation
- "Check Label" button to search and filter Installomator labels
  <img width="531" height="493" alt="CheckLabel" src="https://github.com/user-attachments/assets/41eae003-eff9-45f4-97b9-945d216f3d46" />


#### Shell Command

Allows execution of simple shell commands.

#### Jamf Inventory Update (Recon)

Allows running a Jamf recon before executing a script that depends on Jamf inventory information.

#### Watch Path

Checks for the presence of:

- A file
- An application

#### Wait for User Entry

Visible only when User Entry is enabled.

Allows Setup Manager to wait for user input before executing subsequent actions.

---

## Settings
<img width="1444" height="787" alt="Capture d’écran 2026-05-24 à 23 51 48" src="https://github.com/user-attachments/assets/8608df72-e352-4ec2-8e51-d7c21f77c008" />

The Settings menu allows you to configure:

### Global Icon Catalog

Defines the default online icon catalog.

### Project-Specific Icon Catalog

You can also define a project-specific icon catalog saved inside the project itself.

The project catalog can optionally be merged with the global catalog.

### Local Image Folder

Allows Browse buttons to point directly to a local image repository.

Useful when images are deployed locally using a package.

### Autosave

Automatic project save every:

- 1 minute
- 5 minutes
- 10 minutes

---

# Useful Shortcuts

| Shortcut | Action |
|---|---|
| Command + Control + Shift + E | Launch or quit Setup Manager in Debug Mode |
| Command + O | Open Project |
| Command + I | Import plist |
| Command + M | Import mobileconfig |
| Command + E | Export plist |
| Command + S | Save project |
| Command + W | Close window |

---

# Download

Download the latest notarized package from:

https://github.com/YannMarchesseau/JSMmaker2/releases

---

# Credits

Developed by Yann Marchesseau  
WalkingBucket Studio
Website: https://walkingbucket.fr
LinkedIn : https://www.linkedin.com/in/yann-marchesseau-1b44b6119/

# Special thanks to Appitel for authorizing the continuation and public release of this project.
<img width="300" height="90" alt="LogoAppitel" src="https://github.com/user-attachments/assets/613097e0-2505-4af6-b28b-68cbefc48794" />

Appitel is a Paris-based IT services company specialized in Apple device management and Jamf deployments.

Website: https://www.appitel.fr

LinkedIn: https://www.linkedin.com/company/appitel/
