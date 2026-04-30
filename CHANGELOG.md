# Changelog

All notable changes to the Lenses.io for VS Code extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [6.2.2] - 2026-04-30

### Features

- **Schema Registry** — Full schema registry management added to the extension: browse subjects per environment, view schemas in VS Code's native JSON editor, create new subjects with schema validation and autocompletion, edit existing schemas, delete subjects and individual versions, and toggle favourites. The tree view shows a Schema Registry node under each environment with inline create, refresh, and listing actions.
- **Schema Registry CodeLens** — Opening a Schema Registry subject shows inline actions directly above the document: navigate back to the Schema Registry listing, edit the schema, refresh, browse version history, compare versions, compare across environments, and toggle favourites. Version-related actions appear only when a subject has multiple versions.
- **Schema Registry Version History & Comparison** — Browse all versions of a schema subject and compare any two versions side by side using VS Code's native diff editor. Cross-environment comparison lets you diff the same subject between staging and production.
- **Schema Registry in Global Search** — Schema Registry subjects are now indexed and searchable in the global search panel. The post-indexing summary view shows schema counts alongside topics and other entity types.
- **Schema Registry Copilot Tool** — New `#lensesExtensionSchema` language model tool for managing schema registry subjects from Copilot Chat. Supports direct-diff comparison by specifying both versions or both environments without interactive prompts.
- **One-click Community Edition Install** — The welcome screen now offers a one-click Docker install for Lenses Community Edition, letting new users get started without leaving VS Code.

### Improvements

- Schema Registry listing refreshes optimistically after create/delete operations
- Scoped tree refresh for Schema Registry nodes (avoids full tree reload)
- Schema registry references added across search UI and documentation

### Fixed

- **Schema Registry cross-environment comparison** — The generic "Compare" CodeLens for Schema entities now correctly routes to the `schemaSubject` comparison flow instead of `topicSchema`.
- **IAM listing panels crash** — Fixed "cannot read configuration" error when opening IAM listing panels.
- **Search help buttons unresponsive** — Fixed search help buttons not responding to clicks and quick pick icons being misaligned.
- Unused telemetry wired correctly for schema registry operations; placeholder code removed.

---

## [6.2.1] - 2026-04-17

### Features

- **Live Streaming in Pinned SQL Results** — Pinning a running live-data query now transfers the active streaming session to the pinned tab, so records keep flowing while the bottom SQL Results view resets to idle. The pinned tab shows a LIVE/STOPPED indicator, a Stop Query button, and a Go-to-Query button. Stopping or closing from any surface synchronizes all controls.
- **Actionable Health Notifications** — Health notifications now include remediation guidance: consumer lag documents suggest checking consumer health and scaling, connector documents include error traces and restart steps, environment documents suggest checking agent status. Context-specific CodeLens actions (e.g. "Restart Connector", "Open SQL Query") appear directly in health documents.
- **Quick Fix Actions in Problems Panel** — The lightbulb in the Problems panel now shows useful quick fixes: consumer lag issues offer "View Consumer Details" and "Open SQL Query"; failed connectors offer "Restart Connector" and "View Connector Details"; disconnected environments offer "View Environment Status".
- **Full Topic Context Menu on Favourited Topics** — Favourited topics now display the same context menu as topics under each environment, including Data Snapshot, Live Data, Schema, Consumers, Configuration, Insert Messages, Compare Across Environments, and Delete Topic.
- **Context-aware Favourites** — The topic menu dynamically shows "Remove from Favourites" or "Add to Favourites" based on the current state.

### Improvements

- Consistent topic menu ordering across right-click and quick pick menus
- Severity breakdown in the Notifications sidebar (e.g. "4 errors, 10 warnings")
- Click any notification to navigate directly to the health document
- Inline View Details button on every active notification for one-click navigation
- Green SQL Run Query button for better visibility in the editor title bar
- User-friendly API error messages extracted from response bodies instead of generic HTTP status codes

### Fixed

- README screenshots now display correctly on the VS Code Marketplace
- Stale active notifications no longer accumulate after extension restart
- NaN no longer displayed in consumer lag health documents when data is missing
- OAuth sessions no longer cleared by proxied 401 responses from downstream environments
- Stale session data (notification badges, permission cache, search history) cleaned up properly on sign-out
- Environment filter correctly applied when opening Topics from the Environments listing
- Telemetry extension ID and version reporting corrected

### Security

- SSRF origin validation for SSE connections
- Content Security Policy added to Search panels
- innerHTML replaced with safe DOM APIs to prevent XSS
- CSPRNG nonce generation for webview scripts
- Tighter CSP img-src directive (wildcard removed)
- OAuth PKCE verifier stored in SecretStorage
- Infrastructure names hashed in telemetry before transmission

---

## [6.2.0] - 2026-04-07

Initial public release of the Lenses.io for VS Code extension.

### Highlights

- Manage your entire Apache Kafka infrastructure from VS Code: environments, topics, IAM, schemas, and connectors
- Query topics with SQL using VS Code's native editor, with Data Snapshot and Live Data streaming
- Full GitHub Copilot integration with 9 agent tools for natural language Kafka operations
- OAuth 2.0 browser authentication alongside traditional username/password

### Features

- **Environment Management** — Create, configure, and delete Kafka environments with guided workflows, YAML schema validation, and agent deployment assistance
- **Topic Creation** — Create topics with YAML editor, full schema validation, autocompletion for Kafka configuration keys, and automatic tree reveal
- **Topic Insert Messages** — Insert messages with JSON editor, real-time schema validation, AVRO/JSON sample generation, and inline error highlighting
- **SQL Queries** — Query topics with Data Snapshot (historical) or Live Data (real-time streaming) using VS Code's native SQL editor with results in the bottom panel
- **Pin SQL Results** — Snapshot query results into standalone tabs and compare across topics or environments side-by-side
- **IAM Management** — Create, view, edit, and delete Users, Groups, Roles, and Service Accounts with JSON schema validation and dynamic autocompletion
- **Configuration Comparison** — Compare topic configs, schemas, groups, and roles across environments using VS Code's native diff editor
- **Health Monitoring** — Consumer lag warnings, connector failure alerts, and environment connectivity issues surfaced in VS Code's Problems panel with configurable toast notifications
- **Global Search** — Fuzzy search across all entities with filter syntax (`topic:name`, `user:name`, `@env:prod`), search history, starred searches, and configurable indexing
- **Favourites & Saved Queries** — Favourite topics and save SQL queries for quick access, synced with the Lenses.io web app
- **GitHub Copilot Integration** — 9 agent tools for running SQL, opening entities, managing topics, environments, and schema registry subjects, comparisons, search, and more from Copilot Chat (VS Code 1.96+)
- **OAuth Browser Authentication** — Sign in via OAuth 2.0 with your system browser, with automatic token management and refresh
- **Topic Schema Management** — View and edit key/value schemas with version history, version comparison, and full editing capabilities
- **Tree View Navigation** — Browse environments, topics, schemas, connectors, and IAM resources with status indicators, breadcrumb actions, and auto-reveal
- **Open Tabs Sidebar** — Quick access to all open Lenses tabs with click-to-focus and close actions
- **Notifications Panel** — Notification history with active, resolved, and snoozed states, snooze functionality, and status bar badge

### Improvements

- Dynamic autocompletion for role permissions, group members, and user assignments fetched from the API
- Explicit "Apply Changes" button for all entity edits — Cmd+S saves to memory, API mutations require clicking the play button or pressing Cmd+Enter
- Live Data safety guards: pre-connection throughput warnings, automatic record cap, and runtime rate spike detection
- Cancel Connection button to abort authentication at any time without restarting VS Code
- Topic status indicators in the tree: empty topics, data counts, and active throughput
- Auto-append `/api` suffix to Lenses URLs so you can enter just `https://lenses.your-company.com`
- Search index stays consistent after local mutations (creates, edits, deletes) without manual rebuild

### Security

- TLS certificate verification enabled by default for all WebSocket connections (opt-in for self-signed via `lenses.sql.acceptSelfSignedCerts`)
- OAuth client secrets stored in VS Code SecretStorage instead of plaintext settings
- Content Security Policy enforced on all webview panels
- Anonymous telemetry with infrastructure names hashed before transmission (respects VS Code global telemetry setting)

---

**Note:** This is the first public release of the extension. The extension version is aligned with the Lenses.io API version for compatibility (6.2.x extension works with 6.2.y API).
