---
slug: /en/whats-new/cloud
sidebar_label: Cloud Changelog
title: Cloud Changelog
---

In addition to this ClickHouse Cloud changelog, please see the [Cloud Compatibility](/docs/en/cloud/reference/cloud-compatibility.md) page.

## February 2, 2023

This release brings an officially supported Metabase integration, a major Java client / JDBC driver release, and support for views and materialized views in the SQL console.

### Integrations changes
- [Metabase](/docs/en/integrations/data-visualization/metabase-and-clickhouse.md) plugin: Became an official solution maintained ClickHouse
- [dbt](/docs/en/integrations/data-ingestion/etl-tools/dbt/dbt-intro.md) plugin: Added support for [multiple threads](https://github.com/ClickHouse/dbt-clickhouse/blob/main/CHANGELOG.md)
- [Grafana](/docs/en/integrations/data-visualization/grafana-and-clickhouse.md) plugin: Better handling of connection errors
- [Python](/docs/en/integrations/language-clients/python/intro.md) client: [Streaming support](/docs/en/integrations/language-clients/python/queries#streaming-queries) for insert operation
- [Go](/docs/en/integrations/language-clients/go/intro.md) client: [Bug fixes](https://github.com/ClickHouse/clickhouse-go/blob/main/CHANGELOG.md): close canceled connections, better handling of connection errors
- [JS](/docs/en/integrations/language-clients/nodejs.md) client: [Breaking changes in exec/insert](https://github.com/ClickHouse/clickhouse-js/releases/tag/0.0.12); exposed query_id in the return types
- [Java](https://github.com/ClickHouse/clickhouse-java#readme) client / JDBC driver major release
  - [Breaking changes](https://github.com/ClickHouse/clickhouse-java/releases): deprecated methods, classes and packages were removed
  - Added R2DBC driver and file insert support

### Console changes
- Added support for views and materialized views in SQL console

### Performance and reliability
- Faster password reset for stopped/idling instances
- Improved the scale-down behavior via more accurate activity tracking 
- Fixed a bug where SQL console CSV export was truncated
- Fixed a bug resulting in intermittent sample data upload failures


## January 12, 2023

This release updates the ClickHouse version to 22.12, enables dictionaries for many new sources, and improves query performance.

### General changes
- Enabled dictionaries for additional sources, including external ClickHouse, Cassandra, MongoDB, MySQL, PostgreSQL, and Redis 

### ClickHouse 22.12 version upgrade 
- Extended JOIN support to include Grace Hash Join
- Added Binary JSON (BSON) support for reading files
- Added support for GROUP BY ALL standard SQL syntax
- New mathematical functions for decimal operations with fixed precision
- See the [22.12 release blog](https://clickhouse.com/blog/clickhouse-release-22-12) and [detailed 22.12 changelog](/docs/en/whats-new/changelog/2022.md/#-clickhouse-release-2212-2022-12-15) for the complete list of changes

### Console changes
- Improved auto-complete capabilities in SQL Console
- Default region now takes into account continent locality
- Improved Billing Usage page to display both billing and website units

### Integrations changes
- DBT release [v1.3.2](https://github.com/ClickHouse/dbt-clickhouse/blob/main/CHANGELOG.md#release-132-2022-12-23)
  - Added experimental support for the delete+insert incremental strategy
  - New s3source macro
- Python client [v0.4.8](https://github.com/ClickHouse/clickhouse-connect/blob/main/CHANGELOG.md#048-2023-01-02)
  - File insert support
  - Server-side query [parameters binding](/docs/en/interfaces/cli.md/#cli-queries-with-parameters)
- Go client [v2.5.0](https://github.com/ClickHouse/clickhouse-go/releases/tag/v2.5.0)
  - Reduced memory usage for compression
  - Server-side query [parameters binding](/docs/en/interfaces/cli.md/#cli-queries-with-parameters)

### Reliability and performance
- Improved read performance for queries that fetch a large number of small files on object store
- Set the [compatibility](/docs/en/cloud/manage/upgrades.md/#use-the-default-settings-of-a-clickhouse-release) setting to the version with which the service is initially launched, for newly launched services 

### Bug fixes
Using the Advanced Scaling slider to reserve resources now takes effect right away. 

## December 20, 2022

This release introduces seamless logins for administrators to SQL console, improved read performance for cold reads, and an improved Metabase connector for ClickHouse Cloud.

### Console changes
- Enabled seamless access to SQL console for admin users 
- Changed default role for new invitees to "Administrator"
- Added onboarding survey

### Reliability and performance
- Added retry logic for longer running insert queries to recover in the event of network failures
- Optimized backup schedule to run backups only if data was modified
- Improved read performance of cold reads 

### Integrations changes
- The [Metabase plugin](/docs/en/integrations/data-visualization/metabase-and-clickhouse.md) got a long-awaited v0.9.1 major update. Now it is compatible with the latest Metabase version and has been thoroughly tested against ClickHouse Cloud.

## December 6, 2022 - General Availability

ClickHouse Cloud is now production-ready with SOC2 Type II compliance, uptime SLAs for production workloads, and public status page. This release includes major new capabilities like AWS Marketplace integration, SQL console - a data exploration workbench for ClickHouse users, and ClickHouse Academy - self-paced learning in ClickHouse Cloud. Learn more in this [blog](https://clickhouse.com/blog/clickhouse-cloud-generally-available).

### Production-ready
- SOC2 Type II compliance (details in [blog](https://clickhouse.com/blog/clickhouse-cloud-is-now-soc-2-type-ii-compliant) and [Trust Center](https://trust.clickhouse.com/))
- Public [Status Page](https://status.clickhouse.com/) for ClickHouse Cloud
- Uptime SLA available for production use cases
- Availability on [AWS Marketplace](https://aws.amazon.com/marketplace/pp/prodview-jettukeanwrfc)

### Major new capabilities
- Introduced SQL console, the data exploration workbench for ClickHouse users
- Launched [ClickHouse Academy](https://learn.clickhouse.com/visitor_class_catalog), self-paced learning in ClickHouse Cloud

### Pricing and metering changes
- Extended trial to 30 days
- Introduced fixed-capacity, low-monthly-spend Development Services, well-suited for starter projects and development/staging environments
- Introduced new reduced pricing on Production Services, as we continue to improve how ClickHouse Cloud operates and scales
- Improved granularity and fidelity when metering compute

### Integrations changes
- Enabled support for ClickHouse Postgres / MySQL integration engines
- Added support for SQL user-defined functions (UDFs)
- Advanced Kafka Connect sink to Beta status
- Improved Integrations UI by introducing rich meta-data about versions, update status, and more

### Console changes

- Multi-factor authentication support in the cloud console
- Improved cloud console navigation for mobile devices

### Documentation changes

- Introduced a dedicated [documentation](https://clickhouse.com/docs/en/cloud/overview) section for ClickHouse Cloud

### Bug fixes
- Addressed known issue where restore from backup did not always work due to dependency resolution

## November 29, 2022

This release brings SOC2 Type II compliance, updates the ClickHouse version to 22.11, and improves a number of ClickHouse clients and integrations.

### General changes

- Reached SOC2 Type II compliance (details in [blog](https://clickhouse.com/blog/clickhouse-cloud-is-now-soc-2-type-ii-compliant) and [Trust Center](https://trust.clickhouse.com))

### Console changes

- Added an "Idle" status indicator to show that a service has been automatically paused

### ClickHouse 22.11 version upgrade

- Added support for Hudi and DeltaLake table engines and table functions
- Improved recursive directory traversal for S3
- Added support for composite time interval syntax
- Improved insert reliability with retries on insert
- See the [detailed 22.11 changelog](/docs/en/whats-new/changelog/2022.md/#-clickhouse-release-2211-2022-11-17) for the complete list of changes

### Integrations

- Python client: v3.11 support, improved insert performance
- Go client: fix DateTime and Int64 support
- JS client: support for mutual SSL authentication
- dbt-clickhouse: support for DBT v1.3

### Bug fixes

- Fixed a bug that showed an outdated ClickHouse version after an upgrade
- Changing grants for the "default" account no longer interrupts sessions
- Newly created non-admin accounts no longer have system table access by default

### Known issues in this release

- Restore from backup may not work due to dependency resolution

## November 17, 2022

This release enables dictionaries from local ClickHouse table and HTTP sources, introduces support for the Mumbai region, and improves the cloud console user experience.

### General changes

- Added support for [dictionaries](/docs/en/sql-reference/dictionaries/external-dictionaries/external-dicts.md) from local ClickHouse table and HTTP sources
- Introduced support for the Mumbai [region](/docs/en/cloud/reference/supported-regions.md)

### Console changes

- Improved billing invoice formatting
- Streamlined user interface for payment method capture
- Added more granular activity logging for backups
- Improved error handling during file upload

### Bug fixes
- Fixed a bug that could lead to failing backups if there were single large files in some parts
- Fixed a bug where restores from backup did not succeed if access list changes were applied at the same time

### Known issues
- Restore from backup may not work due to dependency resolution

## November 3, 2022

This release removes read & write units from pricing (see the [pricing page](https://clickhouse.com/pricing) for details), updates the ClickHouse version to 22.10, adds support for higher vertical scaling for self-service customers, and improves reliability through better defaults.

### General changes

- Removed read/write units from the pricing model

### Configuration changes

- The settings `allow_suspicious_low_cardinality_types`, `allow_suspicious_fixed_string_types` and `allow_suspicious_codecs` (default is false) cannot be changed by users anymore for stability reasons.

### Console changes

- Increased the self-service maximum for vertical scaling to 720GB memory for paying customers
- Improved the restore from backup workflow to set IP Access List rules and password
- Introduced waitlists for GCP and Azure in the service creation dialog
- Improved error handling during file upload
- Improved workflows for billing administration

### ClickHouse 22.10 version upgrade

- Improved merges on top of object stores by relaxing the "too many parts" threshold in the presence of many large parts (at least 10 GiB). This enables up to petabytes of data in a single partition of a single table.
- Improved control over merging with the `min_age_to_force_merge_seconds` setting, to merge after a certain time threshold.
- Added MySQL-compatible syntax to reset settings `SET setting_name = DEFAULT`.
- Added functions for Morton curve encoding, Java integer hashing, and random number generation.
- See the [detailed 22.10 changelog](/docs/en/whats-new/changelog/2022.md/#-clickhouse-release-2210-2022-10-25) for the complete list of changes.


## October 25, 2022

This release significantly lowers compute consumption for small workloads, lowers compute pricing (see [pricing](https://clickhouse.com/pricing) page for details), improves stability through better defaults, and enhances the Billing and Usage views in the ClickHouse Cloud console.

### General changes

- Reduced minimum service memory allocation to 24G
- Reduced service idle timeout from 30 minutes to 5 minutes

### Configuration changes

- Reduced max_parts_in_total from 100k to 10k. The default value of the `max_parts_in_total` setting for MergeTree tables has been lowered from 100,000 to 10,000. The reason for this change is that we observed that a large number of data parts is likely to cause a slow startup time of services in the cloud. A large number of parts usually indicates a choice of too granular partition key, which is typically done accidentally and should be avoided. The change of default will allow the detection of these cases earlier.

### Console changes

- Enhanced credit usage details in the Billing view for trial users
- Improved tooltips and help text, and added a link to the pricing page in the Usage view
- Improved workflow when switching options for IP filtering
- Added resend email confirmation button to the cloud console

## October 4, 2022 - Beta

ClickHouse Cloud began its public Beta on October 4th, 2022. Learn more in this [blog](https://clickhouse.com/blog/clickhouse-cloud-public-beta).

The ClickHouse Cloud version is based on ClickHouse core v22.10. For a list of compatible features, refer to the [Cloud Compatibility](/docs/en/cloud/reference/cloud-compatibility.md) guide.
