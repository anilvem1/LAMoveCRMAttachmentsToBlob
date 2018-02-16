# Move file attachments from Dynamics 365 to Azure Blob
Move Dynamics 365 Customer Engagement aka CRM Online attachments (Notes attachments / Email Activity Mime attachments) to Azure Blob storage using Azure Logic Apps.
It would be ideal to test run the these Logic Apps in your pre - production environments before using in your production environment.

## Description:
As a customer, I would like to move all my existing CRM attachments stored in Notes / Emails to an Azure Blob as a one time / continuous setup.

These Logic Apps can be used together with the Attachment Management solution available in <a href="https://appsource.microsoft.com/en-us/product/dynamics-365/microsoft_labs.96257e65-dbbe-43db-b775-77cf1609530c">AppSource</a>.

## Move CRM Note Attachments to Azure Blob:
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fccrmappsource.blob.core.windows.net%2Flogicappstemplates%2FLA-MoveCRMNote-AttachmentsToBlob.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Move CRM Email Attachments to Azure Blob:
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fccrmappsource.blob.core.windows.net%2Flogicappstemplates%2FLA-MoveCRMEmail-AttachmentsToBlob.json" target="_blank">
<img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Move CRM Email Attachments By CreatedOn to Azure Blob:
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fccrmappsource.blob.core.windows.net%2Flogicappstemplates%2FLA-MoveCRMEmailByDate-AttachmentsToBlob.json" target="_blank">
<img src="http://azuredeploy.net/deploybutton.png"/>
</a>

#### Note:
To update the start and end dates for CreatedOn for email records, go to Logic App Code view -> Line 111 -> "$filter": "attachmentcount gt 0 and createdon gt 2017-01-01T00:00:00Z and createdon lt 2018-01-01T00:00:00Z",

## Pre requisites:
Create the below containers in Azure Blob storage
1) notesattachments
2) emailattachments
- Note: User can have his own container names updated in Logic Apps via Code view

## Deployment steps

You can click the "Deploy to Azure" button at the beginning of this document.
- Enter the Azure subscription / Resource group / Region
- Enter the Logic App name
- Enter the name / display name of Dynamics CRM connection
- Enter the name / display name of Azure Blob connection
- Enter the Azure storage account name
- Enter the Azure Storage account Access key
- Click 'I agree to the terms and conditions stated above'
- Click Purchase

## Usage

Once the deployment is completed, you can perform below steps to test your Logic App:
- Open the Logic App -> API Connections
- Open CRM API connection -> Click Authorize and save
- Run the Logic App and validate the attachments from CRM to Azure Blob
- Open Logic App in Code View -> find the text 'CRMORGUNIQUENAME_TOBE_REPLACED' and replace it with your CRM organization unique name
- Make sure the the CRM org unique name is having correct extension based on region. (Ex: NA its crm , Australia its crm6 and so on)
- Recurrence: Change the recurrence schedule of Logic App as per your requirement to make it schedule job
- Note: By default, Logic App moves top 2 attachment records ("$top": 2) to Azure Blob. Please update the Logic App in code view with the number you wanted

## Important: 
If you have Attachment Management solution installed from AppSource, please disable the RetrieveMultiple / Update plugin steps on Note & ActivityMimeAttachment entities to avoid any performance issues.
