---
Title: cloud-based-load-testing
Description: This project is owned by HCL Tech System Software team to support the Cloud based Load & Performance Testing on AWS.
Owner of the Project: HCL Tech System Software Team
Contributor: HCL Tech System Software Team
Mail To: hcl_ss_oss@hcl.com
Tags: Load Testing, Performance Testing, Cloud based Load Testing, Cloud based Performance Testing, Cloud based Load & Performance Testing
Created:  2020 Jun 09
Modified: 2020 Jun 09
---

# cloud-based-load-testing


## Objective of Load and Performance Test

Load and Performance tests are needed to validate the size of the actual or required hardware for deployment of Web Application(s) or HTTP(s) based API. Applications which are running over internet will give the minimum CPU and memory utilization if in case single user is using. In case of concurrent user conditions this looks totally different and will give too high system resources utilization and has an adverse impact over the response time. Companies are cutting their IT infrastructure costs as oversized hardware resources are too much expensive and difficult to afford. To achieve this Load and Performance tests will help to find the actual or appropriate size of the required hardware resources.    

From an operational perspective, it’s essential to understand how and when a service or application starts to fail under certain workload situations. There are spiky Black Friday load scenarios or permanent high usage figures which could lead to serious issues. The companies need more temporary IT capacity, while the latter has different demands and requires a permanent increase in capacity. Load and Performance tests are the only measure which gives insights into these critical scenarios.

Performance testing is the name for tests that check how the system behaves and performs. Performance testing examines responsiveness, stability, scalability, reliability, speed and resource usage of the software (like Web Application(s) or HTTP(s) based API) and infrastructure. Performance testing comes in picture when there is the need to check the Web Application(s) or HTTP(s) based API performance, as well as servers, databases, networks, etc.
Load testing is a subset of Performance testing that checks how systems function under a heavy number of concurrent virtual users performing transactions over a certain period of time.

Load and Performance tests are an excellent investment, primarily because they help build trust in the IT services and gives confidence to the organizations that the new or changed system performs within the agreed boundaries.

## Overview of the Project

This project can be used to determine the performance of request(s) traffic coming to the application(s) which are running over internet in form of Web Application(s) or HTTP(s) based API. Based on the outcome metrics the system architect can guide or help the developers to optimize their application code so the response time can be reduced (if possible).

This project provides the platform where AWS services and Taurus (i.e. Open source Docker image for Load and Performance test) will create the virtual traffic and perform the test to identify the gaps or performance issues inside the application(s). Using this project, we can easily understand how our application(s) will be performing at scale and at load and identifying the bottlenecks before releasing the application(s) to production.

The following AWS services have been used in this project:
<pre>
• Elastic Container Registry
• Elastic Container Service
• Fargate
• Lambda
• Simple Storage Service
• DynamoDB
• Simple Queue Service
• Simple Notification Service
• CloudWatch
• API Gateway
• Cognito
• CloudFront
• Virtual Private Cloud
• CodePipeline
• CodeBuild
• Identity and Access Management
• Amplify
• CloudFormation
</pre>

**Please note:**<br>
The published code is in compiled form and it is only supported with AWS. It will be deployed on AWS with the help of CloudFormation.

## How to Deploy the solution on AWS

The following steps will be required to deploy this project over AWS:

**Step1:** Create a new bucket or use a existing bucket from S3.

**Step2:** Clone the repository to local system using git command or download the zip version from the Github.
<pre>
git clone https://github.com/HCLTech-SSW/cloud-based-load-testing.git
</pre>

**Step3:** Using AWS CLI or Amazon console upload the code to existing or newly created S3 bucket (created or specified in Step1
       above).

**Step4:** Edit the “stack-deploy.yaml” for the below set of **_Italics_**, and re-upload the updated file to S3 bucket (created or specified in Step1 
       above).

**S3Bucket:** **_name of source bucket where the cloned git repo will be uploaded_**/<br>
**KeyPrefixHelperService:** **_folder name where the cloned git repo will be uploaded in S3_**/function-as-service/helper-service<br>
**KeyPrefixBackendService:** **_folder name where the cloned git repo will be uploaded in S3_**/function-as-service/backend-service<br>
**KeyPrefixTestResultParser:** **_folder name where the cloned git repo will be uploaded in S3_**/function-as-service/test-result-parser<br>
**KeyPrefixTestRunner:** **_folder name where the cloned git repo will be uploaded in S3_**/function-as-service/test-runner<br>
**KeyPrefixContainer:** **_folder name where the cloned git repo will be uploaded in S3_**/container<br>
**KeyPrefixUserInterface:** **_folder name where the cloned git repo will be uploaded in S3_**/user-interface<br>

**Step5:** From Amazon console go to Amazon CloudFormation and click “Create stack” and select “With new resources (standard)”
       option.

**Step6:** Specify the Amazon S3 URL for template file (location of “stack-deploy.yaml” file in S3 bucket) and click Next.

**Step7:** Specify the mandatory parameters like “Stack name”, “Console Administrator Name” and “Console Administrator Email”. 
       Also please review the “AWS Farget VPC cidr block”, “AWS Farget Subnet A cidr block”, “AWS Farget Subnet B cidr block” 
	   and “AWS Farget SecurityGroup cidr block”.

**Step8:** The stack creation process now starts, and it will deploy the stack on AWS in 10-15 minutes.

**Step9:** Once the creation process is successfully completed, the confirmation email will be send to the email specified in 
       “Console Administrator Email”. That email provides the link of Dashboard, UserID and temporary Password.

**Step10:** Click the Dashboard link, and specify “User Name” and “Password”, it will login to Dashboard.

## How to perform Load & Performance test

**Step1:** Click **CREATE TEST**, and specify the values required for creating test, as shown in the following screenshot (currently fileld with sample values).

![Image1](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image1.png)

![Image2](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image2.png)

![Image3](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image3.png)

**Please Note:**<br>
1. Specify the Web Application URLs/HTTP(s) endpoints with HTTP request method from GET, PUT, POST, and DELETE and specify 
additional information like HTTP Headers and Body Payload data in json format.
2. The confirmation mail will be send to the email id specified in the **Valid Email to Notify**, please confirm the subscription so the test results can be notified over the email (the email subscription is mandatory).

**Step2:** The control will be routed to Dashboard, where the Test entry has been listed in **RUNNING** status.

![Image4](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image4.png)

**Step3:** Click the link under **Details** column, the detailed information related to that Test will be displayed 
       on the screen.
	   
![Image5](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image5.png)

![Image6](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image6.png)

![Image7](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image7.png)

**Step4:** Wait for the Test status to change from **RUNNING** to **COMPLETED**, post completion the status mail will be send to 
       specified email covering the Test Results.

**Stpe5:** After the test status is **COMPLETED** the generated traffic graph and test metrics provides the information for 
       load & performance responses (parameters details described in “About Test Metrics” section).

![Image8](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image8.png)

![Image9](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image9.png)

![Image10](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image10.png)

**Step6:** Test can be modified by clickin on **UPDATE**, where the Test related information can be modified.  

![Image11](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image11.png)

**Step7:** Test can be deleted by clicking on **DELETE** and will need the confirmation for deletion. 

![Image12](https://github.com/HCLTech-SSW/cloud-based-load-testing/blob/master/images/Image12.png)

## About Test Metrics
• **concurrency:** _This parameter gives the average number of Virtual Users running HTTP requests._<br>
• **throughput:** _This parameter provides information about the total count of all sample requests._<br>
• **succ:** _This parameter provides information about the total count of not-failed sample requests._<br>
• **fail:** _This parameter provides information about the total count of failed requests._<br>
• **avg_rt:** _This parameter signifies the average response time in getting the response from the HTTP(s)/Web URLs 
  Endpoints for serving the requests._<br>
• **stdev_rt:** _This parameter provides information about the standard deviation of response time from all the incoming 
  requests._<br>
• **avg_ct:** _This parameter provides information about the average connect time if present in any HTTP request._<br>
• **avg_lt:** _This parameter gives information about the average latency if present in any HTTP request._<br>
• **rc_200:** _This parameter provides the counts for specific response codes here it is HTTP status code 200._<br>
• **perc_0.0 .. perc_100.0:** _This parameter defines the percentile levels for response time, 0 is also minimum response 
  time, 100 is maximum._<br>
• **Bytes:** _This parameter denotes the total download size for the packets sent or received over HTTP._<br>