# Frequently Asked Questions

This page is created to provide answers for ***\*****Frequently Asked Questions*****\***.

## 1) UI Transaction History: Transactions Not Being Displayed (201)

In <https://management-ui-neu-main.northeurope.cloudapp.azure.com/> transactions are not appearing and instead get "**No transaction data found**".

Errors are also seen in the transaction query aggregator.

***\*Steps to reproduce:\****

1. Process file through icap server.

2. Navigate to UI and navigate to request history.

***\*Expected Outcomes\****:

The processed file is observed in the log.

***\*Actual Outcomes\****:

No files are observed and there are errors observed in the transaction query aggregator pod.

Processed File:

![g1](C:\Users\lenovo\Desktop\g1.png)

File in Transaction Store:

![g2](C:\Users\lenovo\Desktop\g2.png)

Transaction view:

![g3](C:\Users\lenovo\Desktop\g3.png)

Error in pod logs:

![p10](C:\Users\lenovo\Desktop\p10.png)

401 error indicates credentials passed between transaction-query-service pod from the transaction-query-aggregator pod are incorrect. Upon further inspection of the secrets it is because the secrets "transactionqueryserviceref" in namespace icap-administration and "transactionqueryservicesecret" in namespace icap-adaptation do not match.

The secret script for this cluster most likely needs updating.

## 2) UI Policy History - Policies Are Not Appearing in Policy History When New Policy (202)

<https://management-ui-neu-main.northeurope.cloudapp.azure.com/>

When updating the policy, the previous policy is not correctly writing to the policy history store.

***\*Reproduction steps:\****

1. Log into UI and navigate to policy page.

2. Update the current policy and publish.

***\*Expected Results:\****

The policy is updated, and the previous policy is now observable in the policy history.

***\*Actual Results:\****

The policy is updated on screen, the previous policy cannot be seen in the policy history, and cannot be seen in file store. There is also a 401 being produced in the policy management API logs.

Error in Pod:

![g4](C:\Users\lenovo\Desktop\g4.png)

Same cause as bug [#201](https://github.com/filetrust/icap-management-ui/issues/201)

401 error indicates credentials passed between policy-update-service pod from the policy-management-api pod are incorrect. Upon further inspection of the secrets it is because the secrets "policyupdateserviceref" in namespace icap-administration and "policyupdateservicesecret" in namespace icap-adaptation do not match.

The secret script for this cluster most likely needs updating.

## 3) Set Policy Not Being Applied to Processed Files (203)

When processing a file on the north Europe main endpoint, the set policy is not being applied correctly.

***\*Reproduction steps:\****

1. Log into UI and navigate to draft policy.

2. Update draft policy to have all word flags set to disallow and publish policy.

3. Process a word document through ICAP server.

***\*Expected Results:\****

The file is blocked and then referred to the NCFS policy.

***\*Actual Results:\****

The file gets sanitised according to default policy, returning 200 ok and a sanitised file.

![g5](C:\Users\lenovo\Desktop\g5.png)

## 4) File Processing: The Processing of a Supported File with Structural Issues Appears Successful (183)

When the attached file is submitted using the Icap client tool, the result is 200 Ok, the transaction log shows it as Safe but when processed in file drop the results is the error: Unable to protect file due to structural issues and the Structural issues reported.

When the transaction record is opened to view details, the error: '**Error Getting Transaction Details**' is displayed.

![g6](C:\Users\lenovo\Desktop\g6.png)

It still comes out as safe in the ICAP. The FileDrop analysis API is using an older version of the engine. Whereas the ICAP is using latest.

The transaction log issue was just to do with the issues were seeing in the event-submission-service. Processed the same file and viewing it in the transaction log no longer shows the error: '**Error Getting Transaction Details**'.

## 5) Icap Processing: The error: 'Error Getting Address Info for Host' is Seen on Many Occasions When Submitting Files via c-icap Client (191)

This can happen on any endpoint randomly and not sure of the reason.

uks qa south:

![g7](C:\Users\lenovo\Desktop\g7.png)

uks-02:

![g8](C:\Users\lenovo\Desktop\g8.png)

Another stakeholder noted: Each time I've seen this error, I've been on the VPN. Once I disconnect from the VPN, connection has been OK.

Issue has been raised with IT.

According to rising VPN problem, it is retested with few endpoints with & without VPN and it seems more to be throwing the error: '**Failed to initialize ci_connection_t object**' when the endpoint is not working.

## 6) Can Not Login to Management UI on North Main Cluster (270)

URL - <https://management-ui-neu-main.northeurope.cloudapp.azure.com/login>

Manage to Port-forward the identity management service to local port 6088.

Run postman script to create user.

Received Email confirmation.

Create Password reset Token using postman script.

Reset the password using Token.

When try to login using those details getting error:

![g9](C:\Users\lenovo\Desktop\g9.png)

- Checked logs of Identity management service - could not see traffic.

- Error in the page indicates that the server was trying to call localhost:80, which is not the correct path to the identity management service.

- Checked config of management-ui - there was no URL set for identity management.

Manage to login after seb deployed the update.
