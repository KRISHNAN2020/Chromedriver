Introduction
PROJECT OVERVIEW

Project overview by project number and name included in this 2503D release are listed in this section : 
PR24044557 -Inbound Notification Services from EWS

This request is to support Inbound Notification Services from EWS Gateway.

EWS Gateway - CXC Processor WinService and Event Hub Processor WinService

This project is designed for receiving inbound notification services from the EWS Gateway and sending the response to the Banking Team. Below is the list of services we consume for inbound notifications:
- OnTokenStatusChange
- OnNewPayment
- OnNewPaymentRequest
- OnPaymentRequestChange
- OnPaymentStatusChange
- DebitNetworkTransactionDetail
- OnContactMethodWarning

**Enhancement of OnNewPayment Notification:**
In this release, we are including the following changes in OnNewPayment Notification:
- OnNewPayment Notification 4.8 with and without Zelle Risk Score
- OnNewPayment Notification 4.8 Voltage Changes
- Multi-version handling of OnNewPayment Notification (versions 4.2 and 4.8)
- 9.1 MQ Uninstall in PROD for CXC Processor WinService and Event Hub Processor WinService Servers




Test Scope and Traceability
ORGANIZATIONAL BUSINESS LINES IMPACTED

The test scope and traceability of the OnNewPayment Notification Enhancement extends to the following organizational business lines, which will be impacted:

- CXC Processor WinService
- Event Hub Processor WinService
- Zelle Inbound Notification Events and Services
- IBM MQ Services for Message Management in Queue

The plan established for the mentioned business lines is to validate that the message processing of OnNewPayment Notification inbound calls is functioning as expected in both the CXC Processor WinService and Event Hub Processor WinService.
 
TEST SCOPE 
TEST SCOPE
OVERVIEW
The test scope outlines the validation of the happy path flows, backward compatibility, and system integrity for the OnNewPaymentNotification messages and the uninstallation process of IBM MQ Messaging service application in production. The focus will be on ensuring proper processing of messages by the CXC Processor WinService and Event Hub Processor WinService, and verifying no errors or exceptions in production logs after voltage changes.

Test Cases
**Happy Path Flow for OnNewPaymentNotification 4.8 Without Zelle Risk Score**
**Happy Path Flow for OnNewPaymentNotification 4.8 With Zelle Risk Score**
**Backward Compatibility for OnNewPaymentNotification 4.2 and 4.8**


-	**Integrity Check for Voltage Changes**
-	**Uninstallation of IBM MQ 9.1  Messaging Service Application**
   - Ensure the successful uninstallation of the 9.1 IBM MQ Messaging service application from the CXC Processor WinService and Event Hub WinService servers.

#### Specific Goals and Objectives
- Confirm that messages for OnNewPaymentNotification 4.8 with and without Zelle Risk Score are processed correctly.
- Verify the processors handle different versions (4.2 and 4.8) of OnNewPaymentNotification seamlessly.
- Ensure system stability and error-free logs post voltage changes for OnNewPaymentNotification.
- Validate the smooth uninstallation of IBM MQ Messaging service application without impacting existing services.

#### Assumptions
- All necessary environments are up and running with appropriate configurations.
- Test data for the OnNewPaymentNotification messages (both 4.2 and 4.8) are available.
- Access to production logs for validation purposes is provided.
- Procedures for uninstalling the IBM MQ Messaging service application are documented.

#### Dependencies
- Access to production environments for executing the tests.
- Availability of necessary test tools and monitoring systems.
- Dependency on the teams responsible for maintaining and providing access to the production logs.





(PR24044557) 2503D
EWS Gateway -  CXC Processor WinService  and Event Hub Processor WinService


No of Changes	    EWS Gateway|Zelle    -  CXC Processor WinService  and Event Hub Processor WinService - OnNewPayment Notification Enhancement Changes	Development Team
1	OnNewPaymentNotification 4.8.	NOW- Aztecs
2	OnNewPaymentNotification 4.8 Voltage Changes.	NOW- Aztecs
3	OnNewPaymentNotification 4.8 and 4.2 Multiversion Support.	NOW- Aztecs
4	MQ 9.1 UnInstall in CXC Processor Winservice and EventHub Winservice’s	NOW- Aztecs


Testing Types / Applications / Method: 


Test Type	Scope of Event type .	Application/Function	Manual / Automated
Functional	OnNewPaymentNotification 4.8.	CXC Processor Winservice and EventHub Winservice	Manual 
Functional	OnNewPaymentNotification 4.8 Voltage Changes.	CXC Processor Winservice  and EventHub Winservice	Manual 
Functional	OnNewPaymentNotification 4.8 and 4.2 Multiversion Support.	CXC Processor Winservice and EventHub Winservice	
Functional	MQ 9.1 UnInstall in CXC Processor Winservice and EventHub Winservice .	CXC Processor Winservice and EventHub Winservice	

 
Performance Testing
We have covered Performance Testing for OnNewPayment Notification 4.8 and 4.2 in CXC Processor Winservice and EventHub Winservice . Totally we have Dumped the Messages via Admin Tool and made sure that each and every messages is Processed successfully without any time delay. Since there is no Message left unprocessed and we are able to see all the messages in the Logs and DB , we Certified the Performance Testing as Passed in Testing Environment . 

Project # / Name	Type of Performance Testing Needed
(select at least one)	SLA	Objective
	None	Load	Stress	Endurance	Failover		
Application Details 	<X or blank>	<X or blank>	<X or blank>	<X or blank>	<X or blank>	<Business Defined Response Times and Throughput>	<Objective and benefits of performance testing>
EWS Gateway -  CXC Processor WinService  and Event Hub   WinService	N/A	Yes	Yes	N/A	Yes	As a result of performance Testing we are able to Observe that the Bulk amount of messages have been Processed successfully in OnNewPayment Notfication without any time Delay and also there’s no message left unprocessed .	We can assure that the Queue Manager can process both OnNewPayment Notification 4.2 and 4.8 in the same manager and also it can withstand the respective Load during the Traffic .


Test approach
TEST METHODS
Test scripts and test cases were created and maintained in Excel sheets. The finalized test cases were then updated in Storyboard and reviewed during the Sprint closure. -  CXC Processor WinService  and Event Hub   WinService  is a server-based service application , So the testing was conducted manually. The testing process has been successful in the BTAT environment.








TESTING KEY PROCESS AREAS / SCHEDULING

Here is a list of the Key Process Areas for the Zelle: (EWS Gateway - CXC Processor WinService and Event Hub WinService)  Project .
Below is the Test Plan, along with scheduling .


Process Area	Start Date (or link to schedule)	End Date
Test Planning	12/24/2024	01/05/2025
Test Case Development	01/06/2025	01/26/2025
Test Environment Preparation	02/03/2025	02/28/2025
Test Data Collation	02/23/2025	02/25/2025
Test Execution	02/25/2025	02/28/2025
Test Results Analysis	02/29/2025	03/02/2025
Defect Management / Analysis	03/02/2025	03/04/2025
QA Signoff / Closure Report distribution	03/05/2025	03/10/2025
Production Implementation	03/16/2025	03/16/2025







Test Data Management :
The following test data has been derived to achieve comprehensive coverage of test conditions. This data is essential for successfully completing testing and falls within the scope of the project (Zelle: EWS Gateway - CXC Processor WinService and Event Hub WinService).


OnNewPaymentNotification4.2

<?xml version="1.0" encoding="UTF-8"?><OnNewPaymentNotification4.2 xmlns="http://clearxchange.com/release4_0"><event-id>8c124085-19d9-4eb4-ac2a-7e5e6cc24ab1</event-id><event-time>2024-05-27T00:10:34.514Z</event-time><payment><payment-id>FE1831245650</payment-id><amount currency="USD">97.89</amount><initiation-time>2024-05-27T00:10:34.514Z</initiation-time><sender><organization-id>FE1</organization-id><sender-id>c2f61fad-eb44-4244-9477-4d85ddfb8776</sender-id><name>KARA AANEMONE</name><sender-type>person</sender-type><sender-fi-instrument>DDA</sender-fi-instrument><address><line1>9384 POODLE LN</line1><city>KAILAU</city><state-or-subdivision-code>HI</state-or-subdivision-code><zip>96734</zip><country-code>USA</country-code></address></sender><product-type>p2p</product-type><real-time>false</real-time><disburser-details/><status><sent/></status><to-known-recipient><recipient-payment-profile-id>44c9dbab-229c-40c0-83ce-3b4c1ace740c</recipient-payment-profile-id><recipient-organization-id>ALQ</recipient-organization-id><recipient-type>person</recipient-type><recipient-fi-instrument>DDA</recipient-fi-instrument></to-known-recipient></payment></OnNewPaymentNotification4.2>


Onnewpayment 4.8 With Zelle Risk Score :


<OnNewPaymentNotification4.8 xmlns="http://clearxchange.com/release4_0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://clearxchange.com/release4_0 sd-schema4_0.xsd"><event-id>9193857496</event-id><event-time>2024-11-07T22:22:23.062Z</event-time><payment><payment-id>FE1651658475</payment-id><amount currency="USD">50.00</amount><initiation-time>2024-11-07T22:22:22.808Z</initiation-time><sender><organization-id>FE1</organization-id><sender-id>paymentTesting</sender-id><name>payment</name><sender-type>person</sender-type><sender-fi-instrument>DDA</sender-fi-instrument><address><line1>456 gjgb dr</line1><line2>456 gjgb dr</line2><city>dallas</city><state-or-subdivision-code>tx</state-or-subdivision-code><zip>76456</zip><country-code>USA</country-code></address></sender><product-type>p2p</product-type><directory-reference-number>CQ1123451100</directory-reference-number><real-time>false</real-time><disburser-details/><status><sent/></status><to-known-recipient><recipient-payment-profile-id>6436af51-cab1-4951-8d73-9a8fb1bb0b59</recipient-payment-profile-id><recipient-organization-id>NVQ</recipient-organization-id><recipient-type>person</recipient-type><recipient-fi-instrument>DDA</recipient-fi-instrument></to-known-recipient></payment><zelle-risk-score><status>success</status><status-code>0</status-code><model><identifier>6000001</identifier><score>0.75</score><reason-code><key>reason1</key><value>no reason</value></reason-code><attribute><key>days_since_profile_update</key><value>-1</value></attribute><attribute><key>link_tkn_to_recip_acct_1d</key><value>0</value></attribute><attribute><key>link_tkn_to_recip_acct_3d</key><value>0</value></attribute><attribute><key>link_tkn_to_recip_acct_7d</key><value>0</value></attribute><attribute><key>nl_email_domain_match</key><value>0</value></attribute><attribute><key>r_token_flips_1d</key><value>0</value></attribute><attribute><key>r_token_flips_30d</key><value>0</value></attribute><attribute><key>r_token_flips_7d</key><value>0</value></attribute><attribute><key>rcomb_avg_trx_14d</key><value>0.00</value></attribute><attribute><key>rcomb_cnt_1d</key><value>0</value></attribute><attribute><key>rcomb_dsnc_first_pay</key><value>0</value></attribute><attribute><key>rcomb_rat_avg3d_7d</key><value>-327.67</value></attribute><attribute><key>rr_amt_14d</key><value>0.00</value></attribute><attribute><key>rr_amt_7d</key><value>0.00</value></attribute><attribute><key>rr_amt_max_12h</key><value>0.00</value></attribute><attribute><key>rr_amt_max_1d</key><value>0.00</value></attribute><attribute><key>rr_amt_max_30d</key><value>0.00</value></attribute><attribute><key>rr_amt_min_60d</key><value>0.00</value></attribute><attribute><key>rr_rat_cnt3d_7d</key><value>-1.27</value></attribute><attribute><key>rr_unq_senders_1d</key><value>0</value></attribute><attribute><key>rr_unq_senders_30d</key><value>0</value></attribute><attribute><key>rr_unq_senders_7d</key><value>0</value></attribute><attribute><key>rr_unq_senders_90d</key><value>0</value></attribute><attribute><key>token_org_tenure</key><value>0.00</value></attribute><attribute><key>token_status_changes_30d</key><value>0</value></attribute><attribute><key>token_tenure</key><value>-1.00</value></attribute><attribute><key>zfc_ato_3rdpty_recv_90d</key><value>0</value></attribute><attribute><key>zfc_flag</key><value>0</value></attribute><attribute><key>zfc_scam_recv_90d</key><value>0</value></attribute><status-code>0</status-code></model></zelle-risk-score></OnNewPaymentNotification4.8>


OnNewPaymentNotification4.8  Without ZelleRiskScore :

<OnNewPaymentNotification4.8 xmlns="http://clearxchange.com/release4_0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://clearxchange.com/release4_0 sd-schema4_0.xsd"><event-id>3624085725</event-id><event-time>2024-11-08T20:41:44.062Z</event-time><payment><payment-id>FE1771945650</payment-id><amount currency="USD">50.00</amount><initiation-time>2024-11-07T22:22:22.808Z</initiation-time><sender><organization-id>FE1</organization-id><sender-id>paymentTesting</sender-id><name>payment</name><sender-type>person</sender-type><sender-fi-instrument>DDA</sender-fi-instrument><address><line1>456 gjgb dr</line1><line2>456 gjgb dr</line2><city>dallas</city><state-or-subdivision-code>tx</state-or-subdivision-code><zip>76456</zip><country-code>USA</country-code></address></sender><product-type>p2p</product-type><directory-reference-number>CQ1138246657</directory-reference-number><real-time>true</real-time><disburser-details /><status><sent /></status><to-known-recipient><recipient-payment-profile-id>856afcc4531b4571afdea9b9cfad3499</recipient-payment-profile-id><recipient-organization-id>F58</recipient-organization-id><recipient-type>small-business</recipient-type><recipient-fi-instrument>DDA</recipient-fi-instrument></to-known-recipient></payment><zelle-risk-score /></OnNewPaymentNotification4.8>


 
Test Environment Preparation

Environment Assigned for QA and Configuration is Listed below with Contact Support and Availability Details . We will be proceeding with Development and Testing in the below Environments  for CXC Processor and Eventhub WinService’s .
Environment	App Server / Configuration	Support Contact	Stability	Availability
QA/ BTAT A	JWCPFTKEHWS01 / JWCPFTKEHWS02	Natheen / Jamuna	100%	100%
QA/ BTAT D	JWCPFTKEHWS01 / JWCPFTKEHWS02	Natheen / Jamuna	100%	100%

QA Team

The table shown below provides the list of QA resource working as a part of this project:

Resource Name	Team	Role
RAJENDRAN KRISHNAN	NOW-AZTECS	PROFESSIONAL


