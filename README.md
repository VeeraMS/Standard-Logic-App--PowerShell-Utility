# Standard-Logic-App--PowerShell-Utility
This PowerShell utility helps you to perform bulk operations such as bulk Cancel, bulk resubmit runs on the Standard Logic App Workflows.

Below are the supported operations with this utility.

1. BulkCancel - Cancel running instances
2. BulkResubmitFailedRuns - Resubmits failed runs
3. BulkResubmitCancelledRuns - Resubmits cancelled runs
4. BulkResubmitSucceededRuns - Resubmits Succeeded runs

**Steps to follow for executing the script:**

1. Copy the PowerShell script to thedesired folder

2. Set up Azure Service Principal - Contributor access on the Subscription. 
 https://blog.jongallant.com/2017/11/azure-rest-apis-postman/
 
3. Open PowerShell with 'Run As administrator Privileges'

4. Run the below command to bypass the execution policy  and accept -Y
       
       Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
       
5. Change the directory to the PowerShell script folder where its available.
      
       cd  'PowerShellScriptFolderPath'
      
6. Execute one of the below commands to perform the specified bulk operation on Standard Logic App workflow

For User Sign-In option:

	.\Standard_LogicApp_Utility.ps1 -SubscriptionId 'Subscription ID' -ResourceGroupName 'Resource Group Name' -LogicAppName 'Logic App Name' -WorkflowName 'WorkflowName' -Operation 'OperationName' -StartTime '2021-08-19T10:47:07.41621Z' -EndTime '2020-11-02T16:38:00.000Z’

For Azure AD SPN:

	.\Standard_LogicApp_Utility.ps1 -ClientId 'ClientId' -TenantId 'TenantId' -Secret 'Client Secret' -SubscriptionId 'SubscriptionId' -ResourceGroupName 'ResourceGroupName' -LogicAppName 'LogicAppName' -Operation 'OperationName' -WorkFlowName 'WorkFlowName' -StartTime '2020-11-02T16:33:00.000Z' -EndTime '2020-11-02T16:38:00.000Z’

7. Log file gets generated in the script folder with the Run ids and their Start time, you may use these to cross verify the operation in the portal

**Parameters definition**:

![image](https://user-images.githubusercontent.com/82495659/130601462-58b65b4d-eb09-4621-8570-1d3cc6dca9c0.png)


**Note:**

1. Not recommended to run directly on the Production environment

2. It is tested with limited test cases and volume of runs, validate this in test environment prior to execute in Production.
