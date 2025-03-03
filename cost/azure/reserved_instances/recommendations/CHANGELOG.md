# Changelog

## v2.17

- Changed internal names of several incident fields to ensure that they are properly scraped for dashboards.

## v2.16

- Changed policy set from `Reserved Instance` to `Reserved Instances` to match other similar policies.
- Added `Scope` incident field.
- Added `Lookback Period` incident field.
- Changed internal names of several incident fields to ensure that they are properly scraped for dashboards.

## v2.15

- Updated policy metadata to facilitate scraping of incidents for Recommendations dashboard
- Modified incident output to facilitate scraping of incidents for Recommendations dashboard

## v2.14

- Fixed subscriptionName empty in the Incident

## v2.13

- Replaced the term **whitelist** with **allowed list**.

## v2.12

- Added `ignore_status [400,403,404]` for API calls to Azure API to ignore errors related to legacy subscription types

## v2.11

- Replaced references `github.com/rightscale/policy_templates` and `github.com/flexera/policy_templates` with `github.com/flexera-public/policy_templates`

## v2.10

- changed subscriptionID and subscriptionName value to accountID and accountName

## v2.9

- Added the following attributes to policy output: instanceFlexibilityGroup, instanceFlexibilityRatio, normalizedSize, recommendedQuantityNormalized
- Fixed indentation to make consistent

## v2.8

- Added subscription name field

## v2.7

- Updated README.md rightscale documentation links with docs.flexera documentation links

## v2.6

- Updated policy to only pull from first subscription to avoid duplicate data. this will fix the shared repeating data

## v2.5

- Added subscription filter option and ability to specify Azure API endpoint

## v2.4

- Ignored: {"code":"400","message":"Cost management data is unavailable for subscription XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX. The offer MS-AZR-0243P is not supported."}
- Ignored: {"code":"404","message":"Cost Management supports only Enterprise Agreement, Web direct and Microsoft Customer Agreement offer types. Subscription XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX is not associated with a valid offer type."}

## v2.3

- Add option to include all Reservation types in one incident
- Add option to filter for Reservation term; 1 year or 3 year

## v2.2

- Support for all Reservation types: ['VirtualMachines', 'SQLDatabases', 'PostgreSQL', 'ManagedDisk', 'MySQL', 'RedHat', 'MariaDB', 'RedisCache', 'CosmosDB', 'SqlDataWarehouse', 'SUSELinux', 'AppService', 'BlockBlob', 'AzureDataExplorer', 'VMwareCloudSimple']
- Added support for Shared subscription reservations
- Prevent incident updates when data doesn't change
- This policy replaces the [older policy](../recommendations) that uses the Azure EA key which was deprecated

## v2.1

- Added default_frequency "daily"

## v2.0

- initial release
