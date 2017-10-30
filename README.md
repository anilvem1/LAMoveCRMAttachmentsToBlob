# LAMoveCRMAttachmentsToBlob

## Description:
Move Dynamics 365 CE attachments (Notes attachments / Email Activity Mime attachments) to Azure Blob storage using Azure Logic Apps.
As a customer, I would like to move all my existing CRM attachments stored in Notes / Emails to an Azure Blob as a one time / continuous setup.

These Logic Apps can be used together with the Attachment Management solution available in <a href="https://appsource.microsoft.com/en-us/product/dynamics-365/microsoft_labs.96257e65-dbbe-43db-b775-77cf1609530c">AppSource</a>.

## Move CRM Note Attachments to Azure Blob:
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fccrmappsource.blob.core.windows.net%2Flogicappstemplates%2FLA-MoveCRMNote-AttachmentsToBlob.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Move CRM Email Attachments to Azure Blob:
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fccrmappsource.blob.core.windows.net%2Flogicappstemplates%2FLA-MoveCRMEmail-AttachmentsToBlob.json" target="_blank">
<img src="http://azuredeploy.net/deploybutton.png"/>
</a>

## Pre requisites:
Create the containers in Azure Blob storage
1) notesattachments
2) emailattachments

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
- Open the Logic App --> API Connections
- Open CRM API connection -> Click Authorize and save
- Run the Logic App and validate the attachments from CRM to Azure Blob
- Recurrence: Change the recurrence schedule of Logic App as per your requirement to make it schedule job
