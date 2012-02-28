Nagios Plugin "check_cloudwatch" usage:

1) install CloudWatch API Tools
   pre-requirement: Amazon CloudWatch API Tools installed
   http://developer.amazonwebservices.com/connect/entry.jspa?externalID=2534&categoryID=88 

2) copy check_cloudwatch script to appropriate directory ($USER1$ = /usr/lib/nagios/plugins/ recommended ) where Nagios user can read.

3) copy aws.cfg to appropriate directory (/etc/nagios/objects/) and register to nagios.cfg
---
cfg_file=/etc/nagios/objects/aws.cfg
---

4) edit aws.cfg 
 - add instance by setting EC2 Instance ID or RDS Instance Name to alias section of the host
 - register instance to region = Hostgroup
 - add host name to service definitions as needed

tips: 
If you call the script every 5 mins, you should better specify 360 sec = 6mins as you might not retrive the last minute data.
Call the script or mon-get-stats command directly if you want to adjust parameters.

history
1.3 - made any "Bytes" unit return in a human readable format - allyunion
1.2 - arguments changed due to support for multiple regions
1.1 - added support to check thresholds are below than norma state
1.0 - 1st release

Disclaimer

This script is provided as is without any guarantees or warranty. Use it at your own risk.

twitter: @j3tm0t0
