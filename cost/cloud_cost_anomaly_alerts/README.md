# Cloud Cost Anomaly Alerts

## What it does

The Cloud Cost Anomaly Alerts policy analyzes the spend in an organization over a specified time period and sends email notifications if anomalies were detected. The cost anomalies are identified using Bollinger Bands. The bands are defined as follows:
The moving average is calculated using a window size specified.
The upper and lower band are calculated as distance of a given number of standard deviations from the moving average.
Any point outside of the bands is considered as anomalous. If multiple cost anomalies are detected for the given dimensions, the data point with the greatest deviation is reported as incident. Additionally, a URL link is provided to a graphical report where all detected anomalies are shown.

## Functional Details

- The policy queries the /anomalies/report endpoint for the bill analysis API and based on the parameters returns values that are deemed anomalies by the API
- The time granularity of the policy is daily, maximum of 31 days

### Input Parameters

- *Time Period* - Number of days to analyze for the policy run.
  - Minimum Value: 1
  - Maximum Value: 31
  - Default: 30
- *Minimum Period Spend* - minimum daily spend needed to record an anomaly as an incident.
  - Minimum Value: 0
  - Default: 1000
- *Cost Anomaly Dimensions* - Dimensions to group data for the analysis. It is possible to provide multiple dimensions.
  - Default: ["Cloud Vendor Account", "Cloud Vendor", "Service"]
  - The IDs or names of Rule Based Dimensions used to group data for analysis. It is possible to provide multiple RBD IDs or names. As a result, data that was not tagged or difficult to tag in the native cloud platform can be visualized better. The new dimensions in Optima will be populated according to your defined rules, so you can view your costs from new perspectives. A common use case is to create several dimensions, such as 'CCO Environments' and 'Product Lines', which are populated with account values.
  - Filters can now be added to the same dimension values. You can filter 1 to 1 value per dimension e.g. Service=AmazonEC2 , Cloud Vendor=AWS , Cloud Vendor Account Name=Flexera-prod.
- *Cost Metric* - Cost metric used for the analysis: amortized vs nonamortized and blended vs unblended costs.
- *Email addresses of the recipients you wish to notify* - A list of email addresses to notify
- *Window Size* - Number of days used in the calculation of the moving average
  - Minimum Value: 0
  - Default: 10
- *Standard Deviations* - The standard deviation number To define the upper and lower Bollinger bands
  - Minimum Value: 0
  - Default: 2
- *Cost Anomaly Limit* - Top n anomalies to detect
  - Default: 10

### Required Flexera Roles

- policy_manager
- billing_center_viewer

### Cost

This Policy Template does not incur any cloud costs.
