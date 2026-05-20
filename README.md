# Swift / SwiftUI Learning Tracker

A single-file, zero-dependency web app for tracking progress through iOS and SwiftUI concepts.

![Swift Tracker screenshot showing dark terminal-style UI with progress bar and concept sections]

## What it is

A local learning dashboard that lives entirely in one `index.html` file. No build step, no server, no accounts — just open it in a browser. Progress and notes are saved to `localStorage`.

## Features

- **Progress tracking** — mark each concept as Not Started → Familiar → Practicing → Confident → Mastered
- **Notes per item** — freeform notes field on every concept, auto-saved as you type
- **Visual progress bar** — colour-coded by level across all sections at a glance
- **Drag & drop** — reorder sections and items by dragging the `⠿` handle
- **Inline editing** — rename sections and items directly in place
- **Export / Import** — back up and restore your progress as JSON
- **Safe migration** — new concept sections added in future versions are appended automatically without touching your existing progress or notes

## Concept sections

| Section | Topics |
|---|---|
| How an iOS App Works | App lifecycle, scene phases, Info.plist |
| Swift Language Essentials | Optionals, protocols, closures, SPM |
| Swift 6 Concurrency | `@MainActor`, `Sendable`, `actor`, `async let`, `TaskGroup`, isolation rules |
| SwiftUI – UI Fundamentals | Views, layout, modifiers, conditional rendering |
| State & Data Flow | `@State`, `@Binding`, `@Observable`, `@EnvironmentObject` |
| Previews | `#Preview` macro, mock data, multi-device |
| Navigation | `NavigationStack`, `TabView`, sheets, deep linking |
| App Architecture – MVVM | View / ViewModel / Model separation |
| Layered Modular SPM Architecture | Core / Feature / App package layering |
| Networking | `URLSession`, `Codable`, error handling, service layer |
| MVVM + Combine | `@Published`, `.sink`, `AnyCancellable`, Combine operators |
| RxSwift Basics | `Observable`, `BehaviorRelay`, `disposeBag`, `flatMap` |
| OpenAPI 3 Spec | `paths`, `components/schemas`, request/response bodies |
| Router + Protocol Extension Pattern | Capability-per-protocol, extension-per-file routing |
| Push Notifications | APNs, `UNUserNotificationCenter`, payload structure |
| Location Services | `CoreLocation`, permissions, `CLLocationManager` |
| Local Data Storage | `UserDefaults`, `SwiftData`, `CoreData`, Keychain |
| Background Services | `BGTaskScheduler`, background URL sessions |
| Branch SDK – Deep Linking | Deferred deep links, Universal Links |
| Fastlane + GitLab CI | `Fastfile` lanes, `.gitlab-ci.yml`, `match` |

## Usage

```bash
# Clone and open — that's it
git clone https://github.com/brightmohan/swift-tracker.git
open swift-tracker/index.html
```

Or just download `index.html` and open it directly.

### Keyboard shortcuts (notes field)
- `Tab` — inserts 4 spaces
- `Escape` — cancel inline edit

### Backup your progress
Use the **↓ export** button to save a JSON snapshot. Use **↑ import** to restore it on another machine or browser.

## Adding new concepts

Edit `DEFAULT_DATA` in the `<script>` block of `index.html`. The `migrate()` function runs on every page load and appends any sections that don't yet exist in a user's saved state — so existing progress is never overwritten.

```js
{ id: uid(), title: 'My New Section', collapsed: false, items: [
  item('First concept — use `backticks` for inline code'),
  item('Second concept'),
]},
```
