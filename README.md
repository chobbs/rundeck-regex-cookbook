# Regex Cookbook Patterns for Rundeck
A quick reference of regular expressions **recipes** you can use to capture common stings and log output using Rundeck log filters. 

**Note**: These examples assume users are familiar with the supporting settings and components of the Rundeck Log Filter feature for logging and variable assignment.

![Regex](https://i0.wp.com/www.adevguide.com/wp-content/uploads/2019/08/regex-questions.png)

## Getting Started
#### Types of Log Filters in Rundeck
A Rundeck Job may define multiple Log Filters to process the output of steps within the workflow. These examples 
will focus on (2) specific types:
* [Key-Value Data](https://docs.rundeck.com/docs/manual/log-filters/key-value-data.html#key-value-data)
* [Multiline Regex Capture](https://docs.rundeck.com/docs/manual/log-filters/multi-line-regex.html#multiline-regex-capture)

Each log filter applys a different regex pattern match aginst the log results. For more details on how the pattern match work, please reference the documentation for an extended explination. 

## Tester Tool
#### Try-out a few examples using the tester tool
Our tester tool is a Rundeck job that you can leverage to run a few examples inline and play a bit with your pattern match. The tester toolcan be found on our RDSE instance. [Give it a try!](https://rdse.runbook.pagerduty.cloud/project/PDT-Huggins/job/show/2f2d51ba-52c9-4072-acfb-c8a76c8b3d6c?) Happy to take/include feedabck for enhancements.

![tool](https://github.com/rundeckpro/scm-center-of-excellence/blob/fc181b234b72d677f29ed9c3f94ea643edb99597/regex/regex-tool.png)

## Examples

#### 1. Disk Usage (df)

* filter-type: `multiline`
* regex-match: `/^.*tmpfs\s*(\w+)/`

Input:
```
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1968008        0   1968008   0% /dev
tmpfs             396516     1488    395028   1% /run
tmpfs            1982568        0   1982568   0% /sys/fs/cgroup
/dev/loop5           256      256         0 100% /snap/jq/6'/
```
Output:

```
tmpfs             396516     1488    395028   1% /run
tmpfs            1982568        0   1982568   0% /sys/fs/cgroup
```

#### 2. Extract IP Address

* filter-type: `key/value`
* regex-match: `/^.+?((?:\d+\.){3}\d+).+$/`

Input:
```
rule family="ipv4" source address="54.246.81.158" reject"
```
Output:

```
54.246.81.158
```

#### 3. Match a URL within a String

* filter-type: `key/value`
* regex-match: `/^.+\s*(https://[-a-zA-Z0-9+&@#/%?=~_|!:, .;]*[-a-zA-Z0-9+&@#/%=~_|].+)/`

Input:
```
please contact us at https://support.rundeck.com/portal
```
Output:

```
https://support.rundeck.com/portal
```


#### 4. Title


#### 5. Titles


#### 6. Title


## Contributors

Thanks to all wonderful people who donated a recipe ([emoji key](https://allcontributors.org/docs/en/emoji-key)):
