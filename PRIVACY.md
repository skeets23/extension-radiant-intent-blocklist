# Radiant Intent Privacy Policy

Last updated: September 11, 2026

Radiant Intent helps users reduce distractions by filtering website content and applying user-selected website restrictions.

## Information the extension handles

- **Browsing URLs:** The extension reads tab and document URLs to apply focus restrictions and filters. A blocked destination is included in the local extension block-page URL so the user can return to it. The extension does not maintain a separate browsing-history log or send browsing URLs to the developer.
- **Website content:** The extension examines page elements and, where a filter requires it, page text to hide distracting content. This processing happens on the user's device. Page content is not sent to the developer or to the optional API services.
- **Settings:** Focus mode, allow and block lists, custom filters, cached built-in filters, and related configuration are stored locally in the browser's extension storage.
- **Optional API configuration:** If the user enables a work-clock or quote integration, the extension stores the endpoint and any API key locally. A work-clock endpoint may contain a user or account identifier. Clock-status responses are used to enforce the focus lock. Quote responses are displayed on block pages.

The extension does not include analytics, advertising trackers, or click, keystroke, or scroll logging. The developer does not receive users' settings, API keys, browsing URLs, or page content.

## External requests and sharing

The extension periodically downloads built-in filter configuration from this project's public GitHub repository. GitHub and its delivery infrastructure receive ordinary connection information, such as the requester's IP address, when serving these requests. No browsing URLs, page content, custom rules, or API keys are attached to filter-update requests.

Optional integrations contact only the HTTPS API endpoints configured by the user:

- The work-clock integration sends a GET request to the configured URL, including any identifier in that URL, with the configured API key in an API-KEY header.
- The quote integration sends a GET request to the configured URL and, if supplied, the configured key in an Authorization: Bearer header.

These API operators receive connection information and the request data described above. Their own privacy policies govern their handling of that information. The extension does not attach the blocked site's URL or content to these requests. API requests omit browser cookies and reject redirects.

Radiant Intent does not sell user data or use it for advertising, creditworthiness, or lending decisions. Data is used only to provide the extension's user-facing focus and filtering features.

## Storage, retention, and security

Settings and API keys remain in local extension storage until changed, removed, replaced by an import, or cleared by uninstalling the extension. Built-in filter caches and operational status information are refreshed as the extension runs.

API keys are not encrypted by the extension. Access to local extension storage is restricted to trusted extension contexts. HTTPS is used for filter updates and optional API requests.

Manual exports contain all saved settings, including API keys, in an unencrypted JSON file. Keep exports private. Export files remain wherever the user saves them, including after uninstalling the extension; the user is responsible for deleting those files and any copies.

## User controls

Users can edit settings, remove optional API configurations, import or export settings, or uninstall the extension. A configured work-clock lock can temporarily prevent settings changes while the user is clocked in or the API cannot be verified. No account with the developer is required.

## Limited Use

Radiant Intent's use of information received from Google APIs adheres to the Chrome Web Store User Data Policy, including its Limited Use requirements. User data is handled only as needed for the prominently described features, and is not used for unrelated purposes.

## Changes and contact

This policy may be updated when the extension's data practices change. The date above identifies the latest revision.

Questions or privacy concerns can be raised through [this repository's issue tracker](https://github.com/skeets23/extension-radiant-intent-blocklist/issues). Issues are public: do not include API keys, private URLs, settings exports, or other sensitive information.
