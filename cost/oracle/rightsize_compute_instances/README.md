# Oracle Rightsize Compute Instances

## What it does

This policy checks for any pending Oracle Cloud Advisor recommendations for underutilized or idle compute instances and generates an incident for each if any recommendations are found. Both incidents created by this policy are emailed to the user.

## Functional Details

- The policy leverages the Oracle Cloud Advisor API to gather any pending recommendations for underutilized or idle compute instances.
- All recommendations are derived from Oracle Cloud Advisor directly and are based on the user's Oracle Cloud Advisor configuration.

## Input Parameters

This policy has the following input parameters required when launching the policy.

- *Email addresses* - Email addresses of the recipients you wish to notify when new incidents are created.
- *Oracle Cloud Tenant ID/Root Compartment* - OCID of the Oracle Cloud root compartment. In most cases, this is the Tenant ID. Example: ocid1.tenancy.oc1..aaaaaaaagk6jz9kt13ycn8bbzsr6oexk9fg0xw2l3pryv8hjsw9eumzx4rcf
- *Oracle Cloud Region* - The primary region of the Oracle Cloud account. Example: us-phoenix-1

## Prerequisites

This policy uses [credentials](https://docs.flexera.com/flexera/EN/Automation/ManagingCredentialsExternal.htm) for connecting to the cloud -- in order to apply this policy, you must have a credential registered in the system that is compatible with this policy. If there are no credentials listed when you apply the policy, please contact your cloud admin and ask them to register a credential that is compatible with this policy. The information below should be consulted when creating the credential.

This policy also requires that [Oracle Cloud Advisor](https://docs.oracle.com/en-us/iaas/Content/CloudAdvisor/Tasks/cloudadvisor-getting_started.htm) is enabled and producing recommendations within the Oracle Cloud Infrastructure environment.

### Credential configuration

For administrators [creating and managing credentials](https://docs.flexera.com/flexera/EN/Automation/ManagingCredentialsExternal.htm) to use with this policy, the following information is needed:

Provider tag value to match this policy: `oracle`

Required permissions for the Oracle policy:

- Allow group [Group] to manage optimizer-api-family in tenancy

[Group] should be replaced with a group that the user associated with the Oracle Cloud credential is a member of.

Note: Oracle Cloud credentials cannot be added in Flexera One; the [Flexera Credential Management API](https://reference.rightscale.com/cred-management/#/Credentials/Credentials_create_oracle) must be used to create the credential.

## Supported Clouds

- Oracle Cloud (OCI)

## Cost

This Policy Template does not incur any cloud costs.
