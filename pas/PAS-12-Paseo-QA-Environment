---
PAS: 12
title: Paseo as Polkadot QA Environment
status: Draft
author: Paseo core group
created: 02-01-2026
replaces: PAS-2 (Runtime Upgrade Process)
---

## Changelog

| Version | Description                      | Author    | Date       |
|---------|----------------------------------|-----------|------------|
| 1.0     | Initial version                  |           | 02-01-2026 |

## Summary

Paseo is officially designated as the Polkadot QA (Quality Assurance) environment. Polkadot runtime releases are tested on Paseo before deployment to Kusama and Polkadot mainnets. This document defines the coordination process between the Polkadot Fellowship and the Paseo Core Team for runtime upgrades.

## Abstract

This PAS establishes Paseo's role as the QA environment in the Polkadot release pipeline. Runtime releases flow from Westend (Parity's development testnet) to Paseo (QA environment) and, upon successful validation, proceed to Kusama and Polkadot mainnets. The Paseo Core Team is responsible for executing a testing process within a 14-day window and reporting results to the Polkadot Fellowship.

## Motivation

After evaluation with the broader community, it was determined that exposing Kusama to runtime releases before a dedicated QA environment introduced unnecessary risk. Paseo is the best candidate to serve as this QA environment because it already hosts real parachain teams actively testing their applications and maintains a robust set of validators supporting the network.

## Specification

### Release Pipeline Position

Paseo occupies the QA position in the Polkadot release pipeline:
```
Westend          →    Paseo           →    Kusama/Polkadot
(Development)         (QA - 14 days)       (Production)

Parity Testnet        Polkadot Testnet     Mainnets
Unstable              Stable               Production
```

Paseo runtime follows Polkadot runtime and receives release candidates before Kusama.

### Release Trigger

A new Paseo release cycle begins only from a Polkadot Fellowship release:

1. A Fellowship member tags the Paseo Core Team members in the official Fellowship Element channel
2. The tag must confirm the release is ready for QA testing
3. Upon acknowledgment, the 14-day testing window begins

### Testing Window

The Paseo Core Team has a maximum of 14 days to complete the QA process. The testing window includes:

#### Testing Environment

- **TOT (Testnet of a Testnet)**: A dedicated Paseo test instance where initial validation occurs before applying changes to the main Paseo network

#### Automated Testing

| Test Type | Scope | Tools |
|-----------|-------|-------|
| Runtime Upgrades | Relay chain, AssetHub, Coretime | Chopsticks, try-runtime-cli |
| XCM Calls | Cross-chain messaging validation | Chopsticks |
| State Migrations | Migration correctness verification | try-runtime-cli |

#### Validation Checkpoints

The following must be verified post-upgrade on TOT before proceeding to main Paseo:

- Successful epoch change
- Successful era change
- System chain operations (AssetHub, Coretime)
- No regression in core functionality

#### Team Involvement

- **Primary**: Paseo Core Team (R0GUE, Portico, Zondax)
- **As Required**: Related teams may join if the release specifically requires their participation

### Result Notification

Upon completion of testing, the Paseo Core Team delivers a report in the Fellowship Element channel containing:

- **Status**: Pass / Fail
- **Testing Summary**: Tests executed and results
- **Issues Found**: Any bugs or concerns discovered (even if passed)
- **Recommendations**: Actions for ecosystem participants if applicable

### Failure Handling

In case of test failures:

1. **Immediate Notification**: The Paseo Core Team notifies the Fellowship via the Element channel with details of the failure
2. **Diagnosis**: Collaborate with Fellowship to identify root cause
3. **Resolution**: Work to fix affected services on Paseo
4. **Re-testing**: Upon fix availability, re-execute relevant tests
5. **Blocking**: Critical failures block progression to Kusama/Polkadot until resolved

### Communication Protocol

All communication occurs via Element:

| Event | Channel | Responsible Party |
|-------|---------|-------------------|
| Release Ready Signal | Fellowship Channel | Fellowship Member |
| Acknowledgment | Fellowship Channel | Paseo Core Team |
| Status Updates | Fellowship Channel | Paseo Core Team |
| Final Report | Fellowship Channel | Paseo Core Team |
| Failure Notification | Fellowship Channel | Paseo Core Team |

## Roles and Responsibilities

| Actor | Responsibilities |
|-------|------------------|
| **Polkadot Fellowship** | Runtime development, release readiness signal, issue resolution support |
| **Paseo Core Team** | Test execution, upgrade deployment, result reporting, failure notification |
| **Infrastructure Providers** | Node updates per PAS-11 requirements |

## Relationship to Other PAS

| PAS | Relationship |
|-----|--------------|
| PAS-2 (Core Support Model) | Defines supported system chains and SLA |
| PAS-3 (Runtime Upgrade Communication Template) | Templates for ecosystem communication |
| PAS-7 (Hardware Specs) | Infrastructure requirements for testing |
| PAS-11 (Provider Requirements) | Node update requirements (48hr emergency window) |

## Appendix

### A.1 Communication Channels

- **Fellowship Element Channel**: https://matrix.to/#/#fellowship-members:parity.io
- **Paseo Support Channel**: https://matrix.to/#/#paseo-testnet-support:parity.io

