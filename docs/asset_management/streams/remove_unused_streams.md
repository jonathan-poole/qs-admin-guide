---
layout: default
title: Remove Unused Streams
parent: Streams
grand_parent: Asset Management
nav_order: 2
---

# Remove Unused Streams <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>
{:.no_toc}

## Applicable Environments
{:.no_toc}
* All

## Goal
{:.no_toc}

Sometimes we move applications from one stream to another and, we do not notice that the stream is now empty. Or we create a stream waiting for applications get published to it and, they do not get published. It is always a good practice to delete unused Streams.

## Table of Contents
{:.no_toc}

* TOC
{:toc}
-------------------------

## Get List of Unused Streams (Qlik CLI) <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>

The below script snippet requires the [Qlik CLI](../../tooling/qlik_cli.md).

The script will bring all streams and the number of applications inside of each one. The script will then store the output into the location of your choice in either csv or json format.

### Script
```powershell
# Function to collect streams and number of applications inside

# Parameters
# Assumes default credentials are used for the Qlik CLI Connection
$computerName = 'machineName'
$virtualProxyPrefix = '/default' # leave empty if windows auth is on default VP
$filePath = 'C:\'
$fileName = 'output'
$outputFormat = 'json'

$outFile = ($filePath + $fileName + '.' + $outputFormat)
$computerNameFull = ($computerName + $virtualProxyPrefix).ToString()

# Main
Connect-Qlik -ComputerName $computerNameFull -UseDefaultCredentials -TrustAllCerts

$streams = Get-QlikStream -full

$out = @()

$streamCounter=0

foreach($stream in $streams) {
    
    $appCounter=0

    foreach($app in Get-QlikApp -full -filter "Published eq true and stream.name eq '$($stream.name)' ") {
        $appCounter++
    }

    $outLine = "" | Select streamId,streamName,streamCreatedDate,numOfApps
    $outLine.streamId=$stream.id
    $outLine.streamCreatedDate=$stream.createdDate
    $outLine.streamName=$stream.name
    $outLine.numOfApps=$appCounter

    $out+=$outLine

    $streamCounter++
}

If ($outputFormat.ToLower() -eq 'csv') {
  $out | ConvertTo-Csv -NoTypeInformation | Set-Content $outFile
  }  Else {
  $out | ConvertTo-Json | Set-Content $outFile
} 
```

### Example Output
```
[
    {
        "streamId":  "aaec8d41-5201-43ab-809f-3063750dfafd",
        "streamName":  "Everyone",
        "streamCreatedDate":  "2020/03/03 14:41",
        "numOfApps":  1
    },
    {
        "streamId":  "a70ca8a5-1d59-4cc9-b5fa-6e207978dcaf",
        "streamName":  "Monitoring apps",
        "streamCreatedDate":  "2020/03/03 14:41",
        "numOfApps":  2
    },
    {
        "streamId":  "974647c4-84c1-41e3-9589-24fb8f447135",
        "streamName":  "AAI",
        "streamCreatedDate":  "2020/03/03 15:25",
        "numOfApps":  6
    },
    {
        "streamId":  "8850146c-4fc8-46fd-80fc-f4c2bda49c4e",
        "streamName":  "Medical - Pharma",
        "streamCreatedDate":  "2020/03/03 15:26",
        "numOfApps":  6
    },
    {
        "streamId":  "aebcc4a9-ab9a-4a04-b297-9ad3b30153f9",
        "streamName":  "HR",
        "streamCreatedDate":  "2020/03/03 15:27",
        "numOfApps":  2
    },
    {
        "streamId":  "08eefa4c-e28b-4b9d-99b8-28ac131c49c9",
        "streamName":  "Expansion Strategy",
        "streamCreatedDate":  "2020/03/04 12:20",
        "numOfApps":  2
    }
]
```

**Tags**

#monthly
