# AWS Savings Plan Recommendations

This Policy Template leverages the [AWS Savings Plans Purchase Recommendation API](https://docs.aws.amazon.com/aws-cost-management/latest/APIReference/API_GetSavingsPlansPurchaseRecommendation.html). It will raise incidents if AWS has any Savings Plan Purchase Recommendations, whose monthly savings exceeds the *Monthly Savings Threshold* parameter in the Policy.
It will email the user specified in `Email addresses of the recipients you wish to notify`

> *NOTE: This Policy Template must be appled to the **AWS Organization Master Payer** account.*

## Input Parameters

This policy has the following input parameters required when launching the policy.

- *Look Back Period* - Specify the number of days of past usage to analyze.
- *Savings Plan Term* - Specify he Term length for the Savings Plan.
- *Account Number* - The Account number for use with the AWS STS Cross Account Role. Leave blank when using AWS IAM Access key and secret. It only needs to be passed when the desired AWS account is different than the one associated with the Flexera One credential. [more](https://docs.flexera.com/flexera/EN/Automation/ProviderCredentials.htm#automationadmin_1982464505_1123608)
- *Payment Option* - Specify the payment option for the Savings Plan.
- *Savings Plan Type* - Choose between Compute Savings Plans, EC2 Instance Savings Plans or SageMaker Savings Plans
- *Monthly Savings Threshold* - Specify the minimum monthly savings that should result in a Savings Plan purchase recommendation
- *Email addresses to notify* - A list of email addresses to notify
- *Currency Adjustment* - Number to adjust monthly estimated savings by depending on USD conversion (maximum value 5.0)

## Policy Actions

- Send an email report

## Prerequisites

This policy uses [credentials](https://docs.flexera.com/flexera/EN/Automation/ManagingCredentialsExternal.htm) for connecting to the cloud -- in order to apply this policy you must have a credential registered in the system that is compatible with this policy. If there are no credentials listed when you apply the policy, please contact your cloud admin and ask them to register a credential that is compatible with this policy. The information below should be consulted when creating the credential.

## Credential configuration

For administrators [creating and managing credentials](https://docs.flexera.com/flexera/EN/Automation/ManagingCredentialsExternal.htm) to use with this policy, the following information is needed:

Provider tag value to match this policy: `aws`

Required permissions in the provider:

```javascript
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ce:*"
      ],
      "Resource": [
        "*"
      ]
    }
  ]
}
```

## Supported Clouds

- AWS

## Cost

This Policy Template does not launch any instances, and so does not incur any cloud costs.
