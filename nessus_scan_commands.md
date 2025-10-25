# Nessus-only scan workflow and notes

## 1) Networking / Target
- Ensure Metasploitable2 VM is running and reachable.
- Determine target IP on the VM (e.g., `ifconfig` or `ip addr` inside the VM).
- Example: `TARGET_IP=192.168.56.101`

## 2) Create and run a Nessus scan
1. Open Nessus web UI (default `https://localhost:8834` after installation).  
2. Login and create a new scan:
   - Choose **Advanced Scan** or **Basic Network Scan**.
   - Name: `Metasploitable2 - Basic Vulnerability Scan`
   - Targets: `<TARGET_IP>` (or comma-separated list)
   - Credentials: (leave blank for unauthenticated scan) OR supply credentials for authenticated scan (recommended for deeper findings).
   - Policies: Use default policy or a comprehensive policy (e.g., "Advanced Network Scan").
3. Launch the scan.

## 3) Exporting results
- After scan completes, export the report:
  - Format options: `.nessus` (XML), `.pdf`, `.csv`, `.html`
  - Recommended to save both `.nessus` and `.pdf` for attachments and later import.
- Save exported files to `nessus/` within the repo:
  - `nessus/nessus_export_<TARGET_IP>_YYYYMMDD.nessus`
  - `nessus/nessus_export_<TARGET_IP>_YYYYMMDD.pdf`

## 4) Screenshots
- Take screenshots of:
  - The scan overview (severity summary): save as `screenshots/nessus_scan_overview.png`
  - A sample vulnerability details page (evidence/CVEs): save as `screenshots/nessus_vuln_details.png`

## 5) Notes on authenticated vs unauthenticated scans
- Unauthenticated scans are easier to run but find fewer configuration issues.
- Authenticated scans (supply SSH/SMB/DB credentials) require careful handling of credentials (use temporary lab accounts) but return richer results (missing patches, config weaknesses).

## 6) Example filenames (place in repo)
- `nessus/nessus_export_192.168.56.101_2025-10-25.nessus`
- `nessus/nessus_export_192.168.56.101_2025-10-25.pdf`
