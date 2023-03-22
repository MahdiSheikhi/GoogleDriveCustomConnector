# GoogleDriveCustomConnector

Custom Connector for Google Drive in Power Automate to retrieve the 100 largest files

Create a Custom Connector in Power Automate

In Power Automate, follow these steps to create a custom connector:

a. Go to the Power Automate portal (https://flow.microsoft.com/).

b. Click on "Data" in the left-hand menu, and then select "Custom connectors."

c. Click on the "+ New custom connector" button and choose "Create from blank."

d. Enter a name for your custom connector (e.g., "GoogleDriveBigFiles") and click "Continue."


Configure General Information

In the "General" tab of your custom connector, you can add a description, upload an icon, and provide any additional information that you deem necessary.

Configure Authentication

To set up authentication for your custom connector:


a. Click on the "Security" tab.

b. Choose "OAuth 2.0" as the authentication type.

c. Fill in the required fields:


Identity Provider: "Google"

Client ID: [Your Google API OAuth 2.0 Client ID]

Client Secret: [Your Google API OAuth 2.0 Client Secret]

Authorization URL: "https://accounts.google.com/o/oauth2/v2/auth"

Token URL: "https://oauth2.googleapis.com/token"

Refresh URL: "https://oauth2.googleapis.com/token"

Scope: "https://www.googleapis.com/auth/drive.readonly"

d. Click "Create connector" to save the authentication settings.


Configure Actions

In the "Definition" tab, you can define the actions for your custom connector. 

In this case, we'll create an action to retrieve the 100 largest files:

a. Click "New action."

b. Fill in the required fields:

Summary: "Get 100 largest files"


Description: "Retrieve the 100 largest files from Google Drive."

Operation ID: "Get100LargestFiles"

c. Click "Import from sample" to define the request and response format.


Verb: "GET"

URL: "https://www.googleapis.com/drive/v3/files"

Headers: "Authorization" : "Bearer {token}"

Replace "{token}" with the access token obtained during the OAuth 2.0 authentication process.


d. In the "Query" section, add the following parameters:


Key: "pageSize"

Value: "100"

Required: "Yes"

Key: "fields"

Value: "nextPageToken, files(id, name, mimeType, size, createdTime)"

Required: "Yes"

Key: "orderBy"

Value: "quotaBytesUsed desc"

Required: "Yes"

e. Click "Import" to save the request configuration.

f. Click "Update connector" to save the action.


Test the Custom Connector


To test the custom connector:

a. Click on the "Test" tab.

b. Click "New connection" and sign in with your Google account to authenticate the connector.

c. Once connected, choose the "Get 100 largest files" action.

d. Click "Test operation."


If successful, you will receive a JSON response containing the 100 largest files in your Google Drive.


After testing, you can now use the custom connector in your Power Automate flows to retrieve the 100 largest files from Google Drive.
