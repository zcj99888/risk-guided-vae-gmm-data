# processedData

Public processed data package for the Risk-Guided VAE-GMM battery
anomaly-detection reproduction workflow using CF-ARP inputs.

This directory is intended to be uploaded as the root of the public
`risk-guided-vae-gmm-data` repository.

## Format

Each record is stored as a compressed `.npz` file with embedded labels.

This package does not contain complete raw BMS/EMS logs. The original C&I ESS
operational logs are commercial operating records and are subject to data
governance restrictions that prevent unrestricted public redistribution. The
released files are anonymized, sliced processed voltage-window records with the
fields required to regenerate CF-ARP features, deterministic splits, and the
reported reproduction workflows.

## Top-level fields

- `voltage`: `float64 [T, N]`
- `current`: `float32 [T]`
- `time`: string array `[T]`
- `time_s`: `float32 [T]`
- `unit_ids`: string array `[N]`
- `label`: `uint8 [N]`
- `record_id`: string scalar
- `source_group`: string scalar
- `sampling_interval_s`: `float32` scalar

## Conventions

- `label = 0` means normal.
- `label = 1` means anomalous.
- Public filenames are anonymized and do not retain slice-style names.

## Inventory and checksums

- `file_inventory.csv` lists every public record, anonymized identifier,
  relative path, shape fields, sampling interval, and SHA-256 checksum.
- `checksums.sha256` can be verified from this directory with:

```bash
sha256sum -c checksums.sha256
```

## License

This processed-data package is distributed under the Creative Commons
Attribution 4.0 International License (CC BY 4.0). See `LICENSE` for details.

## Current export summary

- Dataset A: 356 records, 49,985 labeled unit samples.
- Dataset B: 130 records, 29,120 labeled unit samples.
- Total: 486 records.
