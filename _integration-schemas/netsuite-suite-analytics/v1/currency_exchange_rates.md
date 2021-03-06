---
tap: "netsuite-suite-analytics"
version: "1"
key: "currency-exchange-rate"

name: "currency_exchange_rates"
doc-link: "https://www.netsuite.com/help/helpcenter/en_US/srbrowser/Browser2020_1/odbc/record/currency_exchange_rates.html"
description: ""

replication-method: "Key-based Incremental"

attributes:
  - name: "{{ system-column.record-hash }}"
    type: "string"
    primary-key: true
    description: |
      {{ system-column.record-hash-netsuite-suite-analytics }}

      {{ integration.netsuite-primary-keys | flatify }}

  - name: "date_last_modified"
    type: "date-time"
    replication-key: true
    description: |
      The time the {{ table.key | replace: "-"," " }} was last modified.

  - name: "anchor_currency_id"
    type: "integer"
    description: ""

  - name: "base_currency_id"
    type: "integer"
    description: ""

  - name: "currency_id"
    type: "integer"
    description: ""

  - name: "currency_rate_id"
    type: "integer"
    netsuite-primary-key: true
    description: ""
    foreign-key-id: "currency-rate-id"

  - name: "currency_rate_provider_id"
    type: "string"
    description: ""

  - name: "currency_rate_type_id"
    type: "integer"
    description: ""
    foreign-key-id: "currency-rate-type-id"

  - name: "date_effective"
    type: "date-time"
    description: ""

  - name: "entity_id"
    type: "integer"
    description: ""
    foreign-key-id: "entity-id"

  - name: "exchange_rate"
    type: "number"
    description: ""

  - name: "is_anchor_only"
    type: "string"
    description: ""

  - name: "update_method_id"
    type: "string"
    description: ""
---