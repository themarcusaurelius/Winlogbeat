## A Lightweight Shipper For Windows Event Logs.

Keeps a pulse on what's happening across Windows-based infrastructure. Winlogbeat streams Windows event logs to your Vizion Elastic App.

### Installation:

#### <b>Option 1.</b> Automated Installation.

### Windows:

1. As administrator, enter the following command in Powershell or download the zip file here.

```
Start-BitsTransfer -Source 'https://github.com/themarcusaurelius/Winlogbeat/archive/master.zip' -Destination 'C:\Users\Administrator\Downloads\Winlogbeat.zip'
```

2. Unzip the package and extract the contents to the `C:/` drive.

3. Back in Powershell, CD into the extracted folder and run the following script:

```
.\installWinlogbeat.ps1
```

4. When prompted, enter your credentials below and click OK.

```css
Kibana URL: _PLACEHOLDER_KIBANA_URL_
Username: _PLACEHOLDER_USERNAME_
Password: _PLACEHOLDER_PASSWORD_
Elasticsearch API Endpoint: _PLACEHOLDER_API_ENDPOINT_
```

This will install and run winlogbeat.

**Data should now be shipping to your Vizion Elastic app. Check the ```Discover``` tab in Kibana for the incoming logs**

<hr>

#### <b>Option 2.</b> Manual Installation.

### Windows:

1. [Download Winlogbeat.](https://artifacts.elastic.co/downloads/beats/winlogbeat/winlogbeat-oss-6.5.4-windows-x86_64.zip)

2. Extract the contents of the zip file into the ```C:\``` drive.

3.  Rename the ```winlogbeat-6.5.4-windows``` directory in the C:\ drive to ```Winlogbeat```.

4. Open a PowerShell prompt as administrator and cd into the ```C:\``` drive.

5. Set the execution policy to be able to run the execution script. CD into the Winlogbeat folder and run the following script:

```
 PowerShell.exe -ExecutionPolicy UnRestricted -File .\install-service-winlogbeat.ps1
```

6. Configure the ```winlogbeat.yml``` file with the correct Vizion.ai credentials.

<i>Tip: The easiest way to do this is to open the file up in a code editor such as Visual Studio Code.</i>

<b>Kibana:</b>

```yaml
setup.kibana
  host: "_PLACEHOLDER_KIBANA_URL_"
  username: "_PLACEHOLDER_USERNAME_"
  password: "_PLACEHOLDER_PASSWORD_"
```

<b>Elasticsearch Output:</b>

```yaml
output.elasticsearch
  hosts: ["_PLACEHOLDER_API_ENDPOINT_"]
```

7. Test the ```winlogbeat.yml``` configuration. In PowerShell, run the following script in the Winlogbeat folder:

```
.\winlogbeat.exe -e -configtest
```

8. Setup pre-configured Dashboards in Kibana.

```
.\winlogbeat.exe setup --dashboards
```

9. Run the program in the foreground to make sure everything is setup:

```
 .\winlogbeat.exe -c metricbeat.yml -e -d "*"
```

10. Once the config has been tested and runs without any ERROR messages, install ```Winlogbeat``` as a service:

```
.\install-service-winlogbeat.ps1
```

11. Test that ```Winlogbeat``` has been installed as a service:

```
service metricbeat
```

12.  Start the ```Winlogbeat``` service as a background process: 

```
start-service winlogbeat
```

**Data should now be shipping to your Vizion Elastic app. Check the ```Discover``` tab in Kibana for the incoming logs**

