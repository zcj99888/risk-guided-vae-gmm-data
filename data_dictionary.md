# Data Dictionary

This package does not contain complete raw BMS logs. It contains anonymized,
sliced public processed voltage-window records.

## `voltage`

Voltage matrix for one record, shaped `[time, unit]` and stored as `float64`.

## `current`

Current trace aligned with `time`.

## `time`

Original time stamps stored as strings.

## `time_s`

Relative time in seconds from the first sample of the record.

## `unit_ids`

Voltage unit names aligned with the second axis of `voltage`.

## `label`

Binary anomaly label aligned with `unit_ids`.

## `record_id`

An anonymized stable record identifier such as `A_000001`.

## `source_group`

An anonymized group identifier used for split reproducibility.

## `sampling_interval_s`

Median sampling interval in seconds for the record.

## `file_inventory.csv`

File-level manifest with one row per public `.npz` record.

- `dataset_id`: Dataset identifier, either `DatasetA` or `DatasetB`.
- `record_id`: An anonymized stable record identifier matching the `.npz`
  payload field.
- `source_group`: An anonymized group identifier used for split
  reproducibility.
- `relative_path`: Path to the record file relative to the processed-data
  repository root.
- `n_points`: Number of time samples in the record.
- `n_units`: Number of voltage units in the record.
- `has_current`: `1` when the aligned current trace is present, otherwise `0`.
- `sampling_interval_s`: Median sampling interval in seconds for the record.
- `sha256`: SHA-256 checksum of the record file at `relative_path`.
