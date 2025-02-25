# Phase 1
Question: In this lab, does your use of these Amazon S3 security features result in additional cost in the account? If so, how much do you estimate that it will cost?
## S3 Pricing
Versioning:
>When you enable versioning on an Amazon S3 bucket, you are charged for every version of an object that is stored.
>Each version of an object is the entire object, not just a diff from the previous version.
>So if you have three versions of an object stored, you are charged for three complete objects.
Service Access Logs> there is no extra charge for enabling server access logging on an Amazon S3 bucket.\
Directory buckets	Free\
Server-side encryption with Amazon S3 managed keys (SSE-S3)	Free\
First 2,000 general purpose buckets per account / Month	Free
## Athena Pricing 
>Total number of queries: 3 per day * (730 hours in a month / 24 hours in a day) = 91.25 queries per month\
Amount of data scanned per query: 1 GB x 0.0009765625 TB in a GB = 0.0009765625 TB\
Pricing calculations:\
Rounding (91.25) = 91 Rounded total number of queries\
91 queries per month x 0.0009765625 TB x 5.00 USD = 0.44 USD\
SQL queries with per query cost (monthly): 0.44 USD\
Total SQL queries cost (monthly): 0.44 USD

# Phase 2
 *securing the network in the AWS Cloud*
 ### VPC Flow Logs
 >The VPC Flow Logs feature can help you understand how inbound and outbound traffic flows through the VPC.\
 The feature also provides monitoring information that will provide insights for how to secure the web server, subnets, and VPC in later tasks.
>

### Pro tip 
Add an inbound rule to allow SSH access to the WebServer instance so that you can use EC2 Instance Connect to connect to the instance.

To discover the IP address range to use as the source for this rule, run the following commands in your AWS Cloud9 IDE:

```
xxxxxxxxxx
sudo yum install -y jq
curl https://ip-ranges.amazonaws.com/ip-ranges.json| jq -r '.prefixes[] | select(.region=="us-east-1") | select(.service=="EC2_INSTANCE_CONNECT") | .ip_prefix' 
```
> Note: AWS publishes a list of AWS IP address ranges. The first command that you ran from the previous code block installed the jq utility on your AWS Cloud9 instance. This utility is used to transform JSON data into a more readable format and print it to standard output. The second command read in the ip-ranges.json file and found the IP address ranges that EC2 Instance Connect uses in the us-east-1 Region, where the WebServer instance is running.

 ## What were the essential configurations you made that enabled internet access from the instance but also secured it?
 
