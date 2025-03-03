# AWS Burstable Instance CloudWatch Utilization Policy

## What it does

This Policy Template gathers AWS CloudWatch data for instances on 30 day intervals. Information on Burst Credits can be found [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/burstable-performance-instances-monitoring-cpu-credits.html). This policy will then take the appropriate actions based on which check fails and resize the instance.

## Functional Details

- This policy identifies all instances reporting performance metrics to CloudWatch whose CPU, Burst Credit Balance, Surplus Burst Credit Balance meet specified thresholds set forth in the parameters.
- The **Exclusion Tag** parameter is a string value. If the exclusion tag is used on an Instance, that Instance is presumed to be exempt from this policy.
- If you get an **N/A** in a field you will need to install the [CloudWatch Agent](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html) on the instance to get those metrics.

## Input Parameters

This policy has the following input parameters required when launching the policy.

- *Allow/Deny Regions* - Whether to treat regions parameter as allow or deny list.
- *Regions* - A list of regions to allow or deny for an AWS account. Please enter the regions code if SCP is enabled, see [Available Regions](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-available-regions) in AWS; otherwise, the policy may fail on regions that are disabled via SCP. Leave blank to consider all the regions.
- *Email addresses to notify* - Email addresses of the recipients you wish to notify when new incidents are created
- *Account Number* - The Account number for use with the AWS STS Cross Account Role. Leave blank when using AWS IAM Access key and secret. It only needs to be passed when the desired AWS account is different than the one associated with the Flexera One credential. [more](https://docs.flexera.com/flexera/EN/Automation/ProviderCredentials.htm#automationadmin_1982464505_1123608)
- *Number of Surplus Credits to alert on* - Number of CPU Surplus Credits to report on, Set to -1 to ignore cpu burst credits
- *Enable checking burst credit balance against max* - checks burst credit balance against max_earnable_credits
- *Exclusion Tag* - Cloud native tag key to ignore instances. Format: Key:Value
- *Cooldown Days* - Days to cooldown between checks of same instance
- *Automatic Actions* - When this value is set, this policy will automatically take the selected action(s).

Please note that the "*Automatic Actions*" parameter contains a list of action(s) that can be performed on the resources. When it is selected, the policy will automatically execute the corresponding action on the data that failed the checks, post incident generation. Please leave it blank for *manual* action.
For example if a user selects the "Resize Instances" action while applying the policy, all the identified instances that didn't satisfy the policy condition will be resized.

## Policy Actions

- Sends an email notification.
- Resizing instances after approval.

## Prerequisites

This policy uses [credentials](https://docs.flexera.com/flexera/EN/Automation/ManagingCredentialsExternal.htm) for connecting to the cloud -- in order to apply this policy you must have a credential registered in the system that is compatible with this policy. If there are no credentials listed when you apply the policy, please contact your cloud admin and ask them to register a credential that is compatible with this policy. The information below should be consulted when creating the credential.

### Credential configuration

For administrators [creating and managing credentials](https://docs.flexera.com/flexera/EN/Automation/ManagingCredentialsExternal.htm) to use with this policy, the following information is needed:

Provider tag value to match this policy: `aws` , `aws_sts`

Required permissions in the provider:

```javascript
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "cloudwatch:GetMetricStatistics",
        "cloudwatch:ListMetrics"
      ],
      "Resource": "*",
      "Condition": {
        "Bool": {
          "aws:SecureTransport": "true"
        }
      }
    }
  ]
}
```

```javascript
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:StartInstances",
        "ec2:StopInstances"
      ],
      "Resource": "arn:aws:ec2:*:*:instance/*",
    },
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeInstances",
        "ec2:DescribeRegions"
      ],
      "Resource": "*"
    }
  ]
}
```

## Supported Clouds

- AWS

## Cost

This Policy Template does not incur any cloud costs.
