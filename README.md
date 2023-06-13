# LOAD-PERFORMANCE-TEST
The Test has two .jmx files. One is with one sampler while the other .jmx file has more samplers for different endpoints.
PROJECT NAME: LOAD PERFORMANCE TEST
VERSION: N/A
DATE OF TEST: 09/06/2023
TESTED BY: VICTOR FRANCIS EBONG

1. Summary:
A load performance test was conducted to verify the server’s performance under a load of 1000 concurrent users (Number of Thread Groups in JMeter), a ramp-up time of 3 seconds and 1 loop count. 
The test was executed in a non-GUI mode and the test result presents an average throughput of 77.98 transactions per second, with an average response time of 8619.75 milliseconds. For this test, the server experienced a maximum response time of 12696 milliseconds, a minimum response time of 4294 milliseconds and a median response time of 8318.5 milliseconds. The error rate was minimal, with only 1 error encountered during the test. The resources utilization were as follows: 
CPU Usage: 100% CPU usage and 100% Maximum frequency 
Disk I/O: 1330 KB/sec and 1% Highest Active Time
Network I/O Usage: 32 Kbps and 0% Network Utilization
Memory Consumption: 1 Hard Faults/sec and 50% Used Physical Memory
However, before loading the server to 1000 users, I started with 100 users, further increased the load to 500 users, then 700 users and noted the respective response time, throughput, and resource utilization.
For the 1000 users, the endpoint was hit with success response message ‘OK’ and response code 200 for 999 users and 1 error with test failure message ‘Test failed: code expected to contain /200/’ and status code of 503 ‘Service unavailable’ was returned.
 
 
Fig. 1: Test Result Summary Overview for 1000 Users

2. Test Environment:
The load performance test carried out on an API endpoint is aimed at assessing the performance of https://reqres.in web application by testing the PATCH endpoint under a load of 1000 users. 
The test environment consisted of:
	Hardware: Lenovo ThinkPad; 250 GB SSD, 8GB RAM; Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz   2.40 GHz; x64-based processor.
	Software: Windows 11 Pro; Dev Version; 64-bit operating system.
	Network configuration: 4G MTN mini router
	Tool: Apache Jmeter 5.5

3. Test Scenarios:
The Test Scenario is to verify load performance test executed with the following data:
- Number of virtual users: 1000
- Load Pattern: A ramp-up time of 3 seconds was used to reach the load of 1000 users.
- Loop Count: A loop count of 1 is used.
- User Activities: 
An excel file with .csv file format was created during the CLI execution that shows different user activities parameters such as: 
	Timestamp
	Elapsed
	Label
	ResponseCode
	ResponseMessage
	ThreadName
	Datatype
	Success
	FailureMessage
	Bytes
	SentBytes
	GrpThreads
	AllThreads
	URL
	Latency
	IdleTime
	Connect.
 
Fig. 2: Screenshot of the .csv file execution result for 1000 users

Again, a folder was created to store the Apache JMeter Dashboard html test execution files which contains the JSON source code file for Statistics, the html index file and other contents files.
In the Test Plan, a response assertion was added to assert the response code of the API endpoint. A Performance Monitor metric collector listener was also added to collect the server’s resource utilization statistics.
 
4. Test Results:
The load performance test results are as follows:
- Response Time:
	Average: 8619.75 milliseconds
	Minimum: 4294 milliseconds
	Maximum: 12696 milliseconds
	Median: 8318.5 milliseconds
	Percentile: 99.90 percentile at 12696ms
- Throughput:
	Average: 77.98 transactions per second
- Error Rate:
	Total errors encountered: 1
	Error rate: 0.10%
- Resource Utilization:
•	CPU Usage: 100% CPU usage and 100% Maximum frequency 
•	Disk I/O: 1330 KB/sec and 1% Highest Active Time
•	Network I/O Usage: 32 Kbps and 0% Network Utilization; With SentBytes rate of 17.36 KB/s and ReceivedBytes rate of 53.07 KB/s 
•	Memory Consumption: 1 Hard Faults/sec and 50% Used Physical Memory
- Scalability Analysis:
The analysis below shows the different response time and throughput of the server at different load levels.
Number of Users
(Thread Group)	Response Times (ms)	Throughput (Transactions/sec)	Request Summary (%)
	Average	Min.	Max.	Median		Pass	Fail
100	2595.73	1226	4232	2545.50	19.81	100	0
500	7056.08	3385	11484	6728.50	42.74	100	0
700	9250.29	5369	12414	9167.00	56.24	99.89	0.14
1000	8619.75	4294	12696	8318.50	77.98	99.9	0.1

The average response time for the request increases for 500 and 700 users and reduces for 1000 users. Also, the minimum response time increases for 500 and 700 users and reduces for 1000 users.
Furthermore, for maximum response time, the table shows that the higher the load, the higher the maximum response time.
Throughputs from the table above, shows that for 100, 500, 700 and 1000 concurrent users, there is increased number of transactions that the server can handle per seconds. 

5. Important Findings:
Based on the load performance test results, the following key findings were observed:
	The system demonstrated acceptable performance under the load of 1000 users.
	The average response time of 8619.75 milliseconds indicates a satisfactory user experience. Test execution screenshot for Response Time Distribution (attached herewith) shows that 28 responses for the PATCH request were between 11300 and 11400 milliseconds and other distributions also shows other different responses which also indicates an acceptable metrics for good performance response time.
	The server/endpoint throughput of 77.98 transactions per second meets the performance requirements and is reliable. However, should more loads be added to the server to exceed 1000 users, the breaking point of the server can be determined (where the throughput will start reducing or degrading).
	The error rate of 0.10% suggests a stable and reliable system.

6. Recommendations:
Although the load performance test for this Application Under Test (AUT) yielded positive results, the following recommendations are provided for further improvement:
i.	For optimization purposes, load balancing and scaling on the server is imperative. This can be done by distributing the load across multiple servers or instances using load balancers. Scaling the infrastructure horizontally by adding more servers or vertically by increasing server resources can help handle increased load and improve response time.
ii.	Test with different load levels: To simulate real world scenario where an unknown number of users can consume the server’s API or hit the endpoint, load testing should be performed with varying load levels to determine the point at which the system starts experiencing performance degradation. This helps identify the system's scalability and capacity limits.
iii.	Network optimization: To reduce the network latency, the client’s system and network bandwidth should be optimized. This is to ensure that network connections are reliable and properly configured. Therefore, optimizing network protocols and infrastructure will help to reduce network overhead and latency.
In conclusion, the load performance test indicates that the system performs well under a load of 1000 users. The endpoint’s response time and throughput meet the expected performance requirements (based on the test environment configuration/setup), ensuring a satisfactory user experience. The minimal error rate reflects the system's stability and reliability. However, the recommended optimizations and configuration changes should be implemented to optimize the server in order to reduce latency, improve response times, and further enhance the overall performance of the server/endpoint.
