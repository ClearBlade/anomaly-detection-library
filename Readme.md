
# ipm package: anomaly-detection

## Overview

Run a self-training anomaly detection algorithm against a given dataset. The selected algorithm is Moving Median Decomposition as seen in this whitepaper for [Anomaly Detection for Predictive Maintenance](https://files.knime.com/sites/default/files/inline-images/Anomaly_Detection_Time_Series_final.pdf). This Library is for identification of items, events or observations which do not conform to an expected pattern or other items in a dataset.

This is an ipm package, which contains one or more reusable assets within the ipm Community. The 'package.json' in this repo is a ipm spec's package.json, [here](https://docs.clearblade.com/v/3/6-ipm/spec), which is a superset of npm's package.json spec, [here](https://docs.npmjs.com/files/package.json).

[Browse ipm Packages](https://ipm.clearblade.com)

## Setup

No configuration required.

## Usage

### Code Services

`ExampleDetectAnomaly` - Runs anomaly detection against an example dataset, returns an array of Anomalies with metadata.

### Code Libraries

`AnomalyDetection` - Core library for detecting anomalies in datasets


## API

### Functions

<dl>
<dt><a href="#AnomalyDetection">AnomalyDetection()</a></dt>
</dl>

Runs a self-training anomaly detection algorithm against a given dataset. The selected algorithm is Moving Median Decomposition as seen in this whitepaper for [Anomaly Detection for Predictive Maintenance](https://files.knime.com/sites/default/files/inline-images/Anomaly_Detection_Time_Series_final.pdf)  







### Typedefs

<dl>
<dt><a href="#Anomaly">Anomaly</a></dt>
<dd></dd>
</dl>

<a name="AnomalyDetection"></a>

### AnomalyDetection()
Detects Anomalies with Moving Median Decomposition
See attached whitepaper for Anomaly Detection for Predictive Maintenance
https://files.knime.com/sites/default/files/inline-images/Anomaly_Detection_Time_Series_final.pdf

Run a self-training anomaly detection algorithm against a given dataset

**Kind**: global function  
**Parameter**: <code>number[]</code> dataset array of numbers  

* [AnomalyDetection()](#AnomalyDetection)
    * [~calibrate()](#AnomalyDetection..calibrate)
    * [~detect()](#AnomalyDetection..detect) ⇒ [<code>Array.&lt;Anomaly&gt;</code>](#Anomaly)
    * [~getCalibration()](#AnomalyDetection..getCalibration) ⇒ <code>Calibration</code>

<a name="AnomalyDetection..calibrate"></a>

#### AnomalyDetection~calibrate()
Use precomputed anomaly detection calibration profile
This can be used to speed up performance for real-time anomaly detection

**Kind**: inner method of [<code>AnomalyDetection</code>](#AnomalyDetection)  
<a name="AnomalyDetection..detect"></a>

#### AnomalyDetection~detect() ⇒ [<code>Array.&lt;Anomaly&gt;</code>](#Anomaly)
Run the algorithm against the provided dataset.

Note: This is the most computation-heavy method in this library

**Kind**: inner method of [<code>AnomalyDetection</code>](#AnomalyDetection)  
**Returns**: [<code>Array.&lt;Anomaly&gt;</code>](#Anomaly) - anomalies - the list of anomalies found in dataset  
**Parameter**: <code>number</code> strictnessOverride (optional) Set the strictness of the anomaly detection  
<a name="AnomalyDetection..getCalibration"></a>

## AnomalyDetection~getCalibration() ⇒ [<code>Calibration</code>](#Calibration)
Fetch the computed anomaly detection calibration parameters

**Kind**: inner method of [<code>AnomalyDetection</code>](#AnomalyDetection)  
**Returns**: [<code>Calibration</code>](#Calibration) - calibration  
<a name="Calibration"></a>

## Calibration
**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| min | <code>number</code> | min value within threshold |
| max | <code>number</code> | max value within threshold |
| strictness | <code>number</code> | how strict the threshold is against the dataset |
| medians | <code>number</code> | intermediary dataset representing the moving medians |
| pointsPerWindow | <code>number</code> | calibration, number of points per processing window. may be increased for larger datasets |
| numWindows | <code>number</code> | calibration metric derived from pointsPerWindow |

<a name="Anomaly"></a>

## Anomaly
**Kind**: global typedef  
**Properties**

| Name | Type | Description |
| --- | --- | --- |
| index | <code>number</code> | index in the provided dataset |
| value | <code>number</code> | value of the data point that is detected as an anomaly |

