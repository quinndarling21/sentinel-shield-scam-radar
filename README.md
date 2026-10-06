# Sentinel Shield Scam Radar

Live campaign view published by Scam Intel: https://quinndarling21.github.io/sentinel-shield-scam-radar/

The page (`index.html`) is static and renders three data files. To update the dashboard, edit the data, add redacted evidence, commit to `main`. Pages redeploys in about a minute.

## data/campaigns.json
```json
{ "refreshed_at": "2026-10-05T07:00:00-07:00", "refreshed_by": "Scam Intel",
  "campaigns": [ { "id": "kebab-id", "name": "Display name", "brand": "Brand impersonated",
    "family": "rule family, e.g. delivery-fee-smishing", "lure": "...", "asks_for": "...",
    "hosts": ["host"], "url_pattern": "host/path*", "hosting_provider": "...",
    "verdict": "scam", "status": "active | contained", "channels": ["SMS","TikTok","X"],
    "sighting_count": 6, "first_seen": "ISO time", "last_seen": "ISO time",
    "thumbnails": ["evidence/<id>/<file>-redacted.png"], "evidence_report": "link",
    "signal_filed_at": "optional ISO time the harvester filed the signal (shows Signal to protection time once contained)" } ] }
```
`status` is `active` until all four lanes are done or skipped, then `contained`.

## data/sightings.json
`{ "sightings": [ { "id": "SGT-0001", "observed_at": "ISO time", "channel": "SMS | TikTok | X | Reddit | YouTube", "campaign_id": "id or null (unclustered)", "brand": "...", "text": "...", "url": "... or null", "host": "... or null", "classifier_label": "...", "source": "Scam Harvester", "linear_issue": "optional link", "evidence": "evidence/... redacted image or null" } ] }`

Unclustered sightings (`campaign_id: null`) show in the Watchlist until they are matched to a campaign.

## data/lanes.json
`lanes` lists the four response lanes. `campaigns.<id>.<lane key>` = `{ "status": "open | in_progress | waiting_approval | done | skipped", "link": "artifact URL", "at": "ISO time", "owner": "...", "note": "optional" }`. A campaign with no entry shows every lane as open.

## evidence/
Redacted images only (handles, avatars, display names, phone numbers blurred). Originals never leave Scam Intel's computer.
