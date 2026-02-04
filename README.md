# TROI v2 — Technician Resources & Operational Index

> **Model:** Licensed, self‑hosted (or privately hosted) software
>
> **Support:** Best‑effort only (no SLA)
>
> **Core Principle:** **The Ledger is the source of truth. Everything else is derived.**

---

## Overview

TROI (Technician Resources & Operational Index) is an **auditable, ledger‑driven inventory and expense tracking system** designed for technician‑centric operations.

The system is built around **immutable, append‑only ledger events** with **FIFO cost accounting**, ensuring that every part movement, usage, and expense can be traced end‑to‑end for audit and compliance purposes.

TROI is intentionally designed as:
- **Internal‑first** software (company‑hosted or privately hosted)
- **Licensed**, not SaaS
- **Best‑effort supported**, with no uptime or response‑time guarantees

---

## Design Philosophy (Locked)

- Ledger‑derived truth (event sourcing)
- Append‑only, immutable records
- FIFO (First‑In, First‑Out) cost accounting
- No reservations — inventory only moves via real events
- Technicians are accountable once inventory is transferred to them
- Parts Manager is the approval authority of record
- UI, alerts, and reports are projections, not authoritative data

---

## Roles

- **System Admin** — user/role configuration, system settings
- **Parts Manager** — owns all parts, invoices, approvals, and transfers
- **Supervisor** — oversees technicians, initiates requests
- **Technician** — consumes parts, records usage
- **Compliance** — read‑only audit and export access

---

## Core Capabilities

### Inventory
- Warehouse inventory
- Technician inventory (per‑technician location)
- Real‑time on‑hand derived from ledger
- No manual quantity edits

### Ledger Events (Immutable)
- RECEIVE
- TRANSFER
- USAGE
- RETURN
- WRITE_OFF / SCRAP
- RMA_RETURN
- POLICY_UPDATE
- REQUEST_* lifecycle events

### Cost Accounting
- FIFO costing
- Exact traceability: usage → receipt batch → invoice
- Store‑level maintenance cost derived from **USAGE only**

### Evidence & Attachments
- Invoice required for RECEIVE
- Evidence required for WRITE_OFF and RMA_RETURN
- Immutable attachments with integrity hashing

### Requests & Approvals
- Requests can be created by Technicians, Supervisors, or Parts Managers
- **All approvals performed by Parts Manager**
- Fulfillment produces real ledger events (no reservations)

### Parts Catalog
- Card/grid view per part:
  - Image
  - Name
  - Part number
  - Warehouse quantity (derived)
- Categories managed by Parts Manager

### Store & Ticket Tracking
- Store format: **DD‑SSS** (2‑digit Division + 3‑digit Store)
- Ticket numbers derived from ServiceNow:
  - User enters numeric portion only
  - System stores as `INC#####`

---

## TROI v2 — Official Roadmap

### Phase 0 — Reset & Baseline
- New v2 repo/project
- PostgreSQL backend
- Docker‑ready layout
- Licensing & support disclaimers

---

### Phase 1 — Foundation Layer (Week 1)
**Goal:** Secure, auditable core

- Identity & RBAC
- Immutable ledger core
- Attachment subsystem
- FIFO costing engine
- Projection framework (on‑hand, alerts)
- Rebuild & verify tooling

---

### Phase 2 — Core Operations (Week 2)
**Goal:** End‑to‑end inventory flow

- Parts catalog + categories
- Warehouse receiving (invoice required)
- Transfers to technicians
- Technician usage posting
- Returns, write‑offs, RMAs

---

### Phase 3 — Requests, Policies & Alerts (Week 3)
**Goal:** Operational control

- Request workflow
- Parts Manager approvals
- Reorder policies:
  - Min threshold
  - Safety stock
  - Reorder quantity
  - Manual lead‑time (informational)
- Low‑stock & safety alerts

---

### Phase 4 — Reporting, Audit & Compliance (Week 4)
**Goal:** Enterprise‑grade auditability

- FIFO‑exact cost reports
- Store‑level expense analytics
- Ledger & attachment exports
- Compliance dashboards
- Access & export audit logs
- Maintenance & read‑only modes

---

## Hosting Model

- Designed for **internal company hosting**
- Can be privately hosted for PoC/demo
- Container‑friendly deployment
- No managed hosting obligations

---

## Support Model

- Best‑effort support only
- No SLA
- No guaranteed response time
- No obligation for emergency fixes

---

## Disclaimer

TROI is designed to **support auditability**, but does **not guarantee regulatory compliance** with any specific standard. Responsibility for deployment, backups, security hardening, and operational procedures lies with the hosting organization.

---

**TROI v2 is built to be explainable, defensible, and safe — even when no one is actively supporting it.**

