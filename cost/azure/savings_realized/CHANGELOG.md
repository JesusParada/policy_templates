# Changelog

## v3.3

- Corrected issue with policy not retrieving cost data on orgs using newer Azure bill connections

## v3.2

- Updated indentation for chart url so it renders corrrectly in the policy incident email

## v3.1

- Updated description for parameters `param_period_start` and `param_period_end`

## v3.0

- Deprecated `auth_rs` authentication (type: `rightscale`) and replaced with `auth_flexera` (type: `oauth2`).  This is a breaking change which requires a Credential for `auth_flexera` [`provider=flexera`] before the policy can be applied.  Please see docs for setting up [Provider-Specific Credentials](https://docs.flexera.com/flexera/EN/Automation/ProviderCredentials.htm)

## v2.3

- Replaced references `github.com/rightscale/policy_templates` and `github.com/flexera/policy_templates` with `github.com/flexera-public/policy_templates`

## v2.2

- Updated image-charts url ton include org id and project id

## v2.1

- Updated policy "summary_template" name, changed legend position
- Updated image-charts url

## v2.0

- Initial Release
