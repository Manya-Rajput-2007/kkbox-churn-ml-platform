# KKBox Data Contract

## Purpose

Define the expected structure and semantic rules for the KKBox churn dataset before implementing ingestion or feature engineering.

The contract is a boundary between external data and the internal ML pipeline.

## Dataset

Initial dataset:

**KKBox Churn Prediction**

Expected source tables:

- `members`
- `transactions`
- `user_logs`

The original dataset may be accessed through Kaggle during the data-processing phase.

## Core Entities

### Members

Customer/member-level information.

Expected role:

- customer identity
- demographic/profile information
- membership/subscription information

### Transactions

Historical subscription and payment transactions.

Expected role:

- subscription events
- payment behavior
- transaction history

### User Logs

Historical user activity.

Expected role:

- engagement behavior
- activity frequency
- temporal engagement patterns

## Prediction Definition

### Prediction Point

An eligible membership-expiry event.

### Observation Window

The previous **90 days** relative to the prediction point.

### Prediction Horizon

**30 days** after the prediction point.

### Target

Binary churn target:

- `1` - customer does not have a valid renewal within 30 days after the eligible membership-expiry event.
- `0` - customer has a valid renewal within that period.

## Temporal Rules

For every prediction point `T`:

```text
Observation window:
[T - 90 days, T]

Prediction horizon:
(T, T + 30 days]