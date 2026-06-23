# EUDAMED Device Monitor — example

Sample input/output for the **[EUDAMED Device Monitor](https://apify.com/yuancore/eudamed-device-monitor)** Apify actor, which turns the EU's public **EUDAMED** medical-device registry (MDR / IVDR) into clean, structured, schedulable data — with a **change-monitoring** mode.

## Why
The public EUDAMED search UI has **no bulk export** of other companies' devices and **no change feed** — you read it one page at a time. The actor reads the **public, no-auth** JSON API (`ec.europa.eu/tools/eudamed/api/devices/udiDiData`), normalizes each device, and — uniquely — with `monitorSince` returns only devices whose `lastUpdateDate` is on/after a date (a daily diff feed). Export to JSON / CSV / Excel.

- 🔗 **Actor:** https://apify.com/yuancore/eudamed-device-monitor
- 📄 [`sample_input.json`](./sample_input.json) — the change-monitoring mode
- 📄 [`sample_output.json`](./sample_output.json) — real records pulled from the public API (company-level; authorised-representative name **redacted by default** for GDPR)

## Fields (per device)
`basicUdi`, `primaryDi`, `uuid`, `deviceName`, `tradeName`, `riskClass`, `manufacturerName`, `manufacturerSrn`, `deviceStatusType`, `applicableLegislation`, `lastUpdateDate`, version info, and more.

## Caveats
Public EU transparency data, reused under **CC BY 4.0** (attribute *European Commission – EUDAMED*). Company-level; **no PII by default**. **Not affiliated with the European Commission.** The public API is undocumented and can change without notice — the actor ships a schema-drift guard for exactly that.
