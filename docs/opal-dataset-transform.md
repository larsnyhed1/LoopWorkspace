# OPAL Snippet: Unique Combinations of Site, Tracking System, Target, and Value

This snippet transforms the input dataset so that each row represents a unique combination of `site`, `tracking_system`, `target_name`, and `value_meters`.

## Input Dataset Columns

| Column | Description |
|---|---|
| `BUNDLE_TIMESTAMP (CET)` | Timestamp of the bundle in CET |
| `site` | Site identifier |
| `tracking_system` | Tracking system identifier |
| `left_camera_serial` | Serial number of the left camera |
| `right_camera_serial` | Serial number of the right camera |
| `target_name` | Name of the target |
| `gauge` | Gauge identifier |
| `value_meters` | Measured value in meters |

## OPAL Snippet

```opal
pick_col site, tracking_system, target_name, value_meters
| statsby group_by(site, tracking_system, target_name, value_meters)
```

### How It Works

1. **`pick_col`** – Selects only the four columns of interest, discarding `BUNDLE_TIMESTAMP (CET)`, `left_camera_serial`, `right_camera_serial`, and `gauge`.
2. **`statsby group_by(...)`** – Groups by all four selected columns, which produces one row per unique combination of `site`, `tracking_system`, `target_name`, and `value_meters`.

## Output Dataset Columns

| Column | Description |
|---|---|
| `site` | Site identifier |
| `tracking_system` | Tracking system identifier |
| `target_name` | Name of the target |
| `value_meters` | Measured value in meters |
