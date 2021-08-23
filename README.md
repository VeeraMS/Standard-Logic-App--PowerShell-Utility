# Standard-Logic-App--PowerShell-Utility
This PowerShell utility helps you to perform bulk operations such as bulk Cancel, bulk resubmit runs on the Standard Logic App Workflows.

The below are the supported operations with this utility.

1. BulkCancel - Cancel running instances
2. BulkResubmitFailedRuns - Resubmits failed runs
3. BulkResubmitCancelledRuns - Resubmits cancelled runs
4. BulkResubmitSucceededRuns - Resubmits Succeeded runs

**Steps to follow for executing the script:**

1. Copy the PowerShell script desired folder

2. Set up Azure Service Principal - Contributor access on the Subscription. 
 https://blog.jongallant.com/2017/11/azure-rest-apis-postman/
 
3. Open PowerShell with 'Run As administrator Privileges'

4. Run the below command to bypass the execution policy  and accept -Y
       
       Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
       
5. Change the directory to the PowerShell script folder where its available.
      
       cd  'PowerShellScriptFolderPath'
      
6. Execute the one of the command below to perform the specified bulk operation on Standard Logic App workflow

For User Sign-In option:

	.\Standard_LogicApp_Utility.ps1 -SubscriptionId '5bbb64a9-f724-405e-bc6b-c8c26aa22551' -ResourceGroupName 'LAV2_HA_DR_PrimaryRegion' -LogicAppName 'LAV2Primary' -WorkflowName 'recurrencetrigger' -Operation 'BulkResubmitCancelledRuns ' -StartTime '2021-08-19T10:47:07.41621Z'

For Azure AD SPN:

	.\Standard_LogicApp_Utility.ps1 -ClientId $ClientId -TenantId $TenantId -Secret $Secret -SubscriptionId $SubscriptionId -ResourceGroupName $ResourceGroupName -LogicAppName $LogicAppName -Operation $Operation -WorkFlowName $WorkFlowName -StartTime '2020-11-02T16:33:00.000Z' -EndTime '2020-11-02T16:38:00.000Z’


**Parameters definition**:

![image](https://user-images.githubusercontent.com/82495659/130448718-875dbd14-a3d9-45cf-8a77-ae9c8a3a0d70.png)


	
7. Validate the text file gets created in the same folder for list of run ids executed
