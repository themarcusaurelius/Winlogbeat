## A Lightweight Shipper For Windows Event Logs.

Keeps a pulse on what's happening across Windows-based infrastructure. Winlogbeat streams Windows event logs to your Vizion Elastic App.

## Installation:

### Windows:

1) As administrator, enter the following command in Powershell or download the zip file [here](https://github.com/themarcusaurelius/Winlogbeat/archive/master.zip).

```
Start-BitsTransfer -Source 'https://github.com/themarcusaurelius/Winlogbeat/archive/master.zip' -Destination 'C:\Users\Administrator\Downloads\Winlogbeat.zip'
```

2) Unzip the package and extract the contents to the `C:/` drive.

3) Back in Powershell, CD into the extracted folder and run the following script:

```
.\installWinlogbeat.ps1
```

4) When prompted, enter your credentials below and click OK.

```css
Kibana URL: _PLACEHOLDER_KIBANA_URL_
Username: _PLACEHOLDER_USERNAME_
Password: _PLACEHOLDER_PASSWORD_
Elasticsearch API Endpoint: _PLACEHOLDER_API_ENDPOINT_
```

This will install and run winlogbeat.

**Data should now be shipping to your Vizion Elastic app. Check the ```Discover``` tab in Kibana for the incoming logs**


