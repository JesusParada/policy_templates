# Changelog

## v3.0

- Added logic required for "Meta Policy" use-cases

## v2.9

- Modified `sys_log` definition to disable `rs_cm.audit_entry.create` outside Flexera NAM
- Replaced references `github.com/rightscale/policy_templates` and `github.com/flexera/policy_templates` with `github.com/flexera-public/policy_templates`

## v2.8

- Added default to aws_account_number parameter to enable existing API users.

## v2.7

- Added support for a single AWS STS Cross account role to be used for multiple policies.

## v2.6

- updated README.md rightscale documentation links with docs.flexera documentation links

## v2.5

- Added default_frequency "daily"

## v2.4

- Modified escalation label and description for consistency

## v2.3

- Added AWS Account ID to resource table

## v2.2

- Adding incident resource table

## v2.1

- remove unnecessary permissions block

## v2.0

- Changes to support the Credential Service

## v1.1

- modified constructing S3 bucket endpoint.

## v1.0

- initial release
