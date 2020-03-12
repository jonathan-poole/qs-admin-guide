---
layout: default
title: Remove Unused Streams
parent: Streams
grand_parent: Asset Management
nav_order: 2
---

# Remove Unused Streams <i class="fas fa-dolly-flatbed fa-xs" title="Shipped | Native Capability"></i> <i class="fas fa-file-code fa-xs" title="API | Requires Script"></i>
{:.no_toc}

## Applicable Environments
{:.no_toc}
* All

## Goal
{:.no_toc}

Sometimes we move applications from one stream to another one and we do not notice that the stream is now empty. Or we create a stream waiting for applications get published to it and it not. It is always a good practice to delete unused Streams.

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

    $streamId= $stream.id
    $streamName = $stream.name

    $outLine = "" | Select streamId,streamName,numOfApps
    $outLine.streamId=$stream.id
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