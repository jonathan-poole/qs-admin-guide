---
layout: default
title: Remove Unused Data Connections
parent: Data Connections
grand_parent: Asset Management
nav_order: 3
---

# Remove Unused Data Connections <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> <i class="fas fa-tools fa-xs" title="Tooling | Pre-Built Solutions"></i> <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>
{:.no_toc}

## Applicable Environments
{:.no_toc}
- Development
- Production

## Goal
{:.no_toc}
Removing unused connections on a regular basis decreases clutter, improves performance, and creates a better user experience. The goal of this section is to leave only the data connections that are necessary for analysis.

## Table of Contents
{:.no_toc}

* TOC
{:toc}
-------------------------

## Data Connection Usage

Data connections are a bit of a difficult entity to map to associated resources, as they are not directly mapped in the QRS to the apps that are using them. Data connections are evaluated in the script, and leveraged at the time of reload. 

There are two primary options for mapping data connections:
- The `lineage` endpoint of an application
  - Accessible via the [Qlik Engine REST API](https://help.qlik.com/en-US/sense-developer/APIs/QIXAPI/index.html?page=8) lineage endpoint, available as of the June 2019 release
  - Accessible via the [Qlik Engine API](https://help.qlik.com/en-US/sense-developer/Subsystems/EngineAPI/Content/Sense_EngineAPI/introducing-engine-API.htm)
- Parsing of evaluated script logs, as demonstrated by the [Data Connection Analyzer](../../tooling/data_connection_analyzer.md)

Pros and cons of the `lineage` option:

| Pros                                                                | Cons                                                                                                                                                                                    |
|---------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Simple to iterate over (the RESTful option) from a Qlik load script | Returns fully evaluated folder paths, so that they cannot be properly mapped back to their respective lib:// connections--ultimately not allowing the mapping of any Folder connections |
| Quick and efficient                                                 | Can be difficult to parse the result                                                                                                                                                    |
| Includes INLINE and AUTOGENERATE loads                              | Does not include any history -- only most recent reload                                                                                                                                 |
|                                                                     | Does not offer insight what user used them when                                                                                                                                         |
|                                                                     | Does not offer insight into how many times they were used                                                                                                                               |
|                                                                     |                                                                                                                                                                                         |
|                                                                     |                                                                                                                                                                                         |
|                                                                     |                                                                                                                                                                                         |
|                                                                     |                                                                                                                                                                                         |

Pros and cons of the [Data Connection Analyzer](../../tooling/data_connection_analyzer.md) option:

| Pros                                                                           | Cons                                                                                           |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| Robust logic to handle all data connection types, including Folder connections | Can take many hours to run the first time, as it can parse thousands of logs                   |
| Has the ability to capture logs from all time                                  | Can potentially produce false positives for unused data connections (see app docs for details) |
| Can be used for comprehensive audit                                            |                                                                                                |
| Tracks what users used what connections when                                   |                                                                                                |
| Tracks how many time data connections have been run                            |                                                                                                |
| Tracks the source of the reload: Hub, Scheduler, or ODAG (api)                 |                                                                                                |
|                                                                                |                                                                                                |
|                                                                                |                                                                                                |
|                                                                                |                                                                                                |

-------------------------

## Unused Data Connections <i class="fas fa-tools fa-xs" title="Tooling | Pre-Built Solutions"></i>

To capture unused data connections, either of the two options from the **Data Connection Usage** section above may be employeed. _If using the `lineage` option, the resulting connections will need to be mapped back to the existing connections in the QRS. Please note the issue with that endpoint and Folder type connections, documented above._

In this section, we will use the [Data Connection Analyzer](../../tooling/data_connection_analyzer.md).

There are two sheets that should be focused on within that application:
- _Used Connections That Have Not Been Used Within 90 Days_
  - This sheet illustrates connections that were at one point active, but sometime over the last 90 days, they have fallen inactive--meaning, there are currently no applications that leverage them. This variable is configurable in the load script, and should be set according to corporate policy.
  `SET vNumDaysForUsedDataConnectionToBeConsideredUnused = 90;`
  
  [![unused_data_connections_native_1.png](images/unused_data_connections_native_1.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/data_connections/images/unused_data_connections_native_1.png)

- _Unused Connection Analysis_
  - This sheet shows connections that have been used, by the only apps that ever used them have been deleted, as well as connections that have never been used.

  [![unused_data_connections_native_2.png](images/unused_data_connections_native_2.png)](https://raw.githubusercontent.com/qs-admin-guide/qs-admin-guide/master/docs/asset_management/data_connections/images/unused_data_connections_native_2.png)

-------------------------

## Suggested Actions

It is suggested that data connections be deleted _manually_, and that all data connections are validated for usage by the owner before deletion. The Data Connection Analyzer is largely accurate, but should not be treated as 100% so--validation must be done with the users. It is also suggested to first "quarantine" the data connections before deleting them. 

### Suggested Quarantine Method

An example of "Quarantining" a data connection can be done by following these steps:

	- Rename the data connection by prepending `QUARANTINED - ` to its name. For example, `My Data Connection (directory_owner)` becomes `QUARANTINED - My Data Connection (directory_owner)`
	- Change the owner of the data connection to `sa_repository`
	- Creating a custom property named `QuarantinedDataConnection` where the value of `true` is applied to any quarantined connection.
	- Modify any existing customized security rules on data connections, leveraging the `QuarantinedDataConnection` custom property to negate them. For example, `((user.group="YourGroup"))` becomes `((user.group="YourGroup" and @QuarantinedDataConnection.Empty()))`.
	
These name change ensures that the data connection cannot be read in an application's script by the scheduler, and owner change confirms that the original owner of the user can no longer read the connection via the default security rule `OwnerRead`, and the security rule modifications ensure that the users cannot read the data connections by some other custom data connection rules if they have a value in the `QuarantinedDataConnection` custom property.

### Priority

1. Connections that have never been used, especially connections that were not created recently. Recently created connections that have never been used simply may not have been used yet--so those should not be removed. Otherwise, these connections are purely clutter, that more than likely were once used for testing connectivity.

2. Connections that were used by applications where the applications have now been deleted. These are more than likely deprecated data sources.

3. Used data connections that haven't been used in "x" days. 

### Data Connection Backup

It might not be the worst idea to take a snapshot of all data connections before removal, in case one needs to be recreated. Data connections are not typically difficult to configure, but it is nice to have to reference in case.

-------------------------

### Scripts to Manage Unused Data Connections

**It is highly recommended to delete data connections manually, after validating with their respective owners. Please refer to the _Suggestions_ section above. The scripts below show how data connections can be backed up and programmatically tagged. The tagging allows them to be essentially _disabled_ using security rules before the data connections are removed.**

#### Script to Backup All Data Connections

```powershell
# Script to backup data connections to json

# Parameters
# Assumes default credentials are used for the Qlik CLI Connection
$computerName = '<machine-name>'
$virtualProxyPrefix = '/default' # leave empty if windows auth is on default VP
$outFilePath = 'C:\'
$outFileName = 'data_connection_backup'

# Main
$outFile = ($outFilePath + $outFileName + '.json')
$computerNameFull = ($computerName + $virtualProxyPrefix).ToString()

Connect-Qlik -ComputerName $computerNameFull -UseDefaultCredentials -TrustAllCerts
Get-QlikDataConnection -raw -full | ConvertTo-Json | Set-Content $outFile
```

#### Script to Tag Data Connections from an Excel Export Containing IDs

```powershell
# Function to import data connection ids from excel and tag them
# Assumes the ImportExcel module: `Install-Module -Name ImportExcel`
# Assumes tag exists, such as 'DataConnectionUnused'
# GUID validation code referenced from: https://pscustomobject.github.io/powershell/functions/PowerShell-Validate-Guid-copy/

# Parameters
# Assumes default credentials are used for the Qlik CLI Connection
$computerName = '<machine-name>'
$virtualProxyPrefix = '/default' # leave empty if windows auth is on default VP
$inputXlsxPath = 'C:\<filename>.xlsx'
$dataConnectionIdColumn = '<name of column containing data connection ID>'
$tagName = '<name of existing tag>'
$outFilePath = 'C:\'
$outFileName = '<output file name>'

# Main
$outFile = ($outFilePath + $outFileName + '.csv')
$computerNameFull = ($computerName + $virtualProxyPrefix).ToString()

if (Test-Path $outFile) 
{
  Remove-Item $outFile
}

function Test-IsGuid
{
	[OutputType([bool])]
	param
	(
		[Parameter(Mandatory = $true)]
		[string]$ObjectGuid
	)
	
	[regex]$guidRegex = '(?im)^[{(]?[0-9A-F]{8}[-]?(?:[0-9A-F]{4}[-]?){3}[0-9A-F]{12}[)}]?$'
	return $ObjectGuid -match $guidRegex
}

$data = Import-Excel $inputXlsxPath -HeaderName $dataConnectionIdColumn -DataOnly
$dataConnectionIds = $data | foreach { $_.psobject.Properties } | where Value -is string | foreach { If(Test-IsGuid -ObjectGuid $_.Value) {$_.Value} }

Connect-Qlik -ComputerName $computerNameFull -UseDefaultCredentials -TrustAllCerts

foreach ($dataConnection in $dataConnectionIds) {
	$resp = Get-QlikDataConnection -id $dataConnection | Update-QlikDataConnection -tags $tagName
	'Tagged: ' + $resp.name + ',' + $dataConnection
	Add-Content -Path $outFile -Value $($resp.name + ',' + $dataConnection)
}
```
