Zelle® Disbursements and Inbound Notification Services
Introduction to Zelle® Disbursements
Zelle® is a fast, safe, and easy way to send and receive money, commonly used for transactions with friends, family, or small businesses. Beyond peer-to-peer payments, Zelle® also enables disbursements—allowing you to receive money from organizations, companies, and even government entities directly into your bank account.

Key Benefits of Zelle® Disbursements
Fast: Funds are sent directly to your bank account, eliminating the wait for checks or prepaid cards.
Safe: Receive money using just an email address or U.S. mobile number—no need to share bank account details.
Easy: If you’re new to Zelle®, enrollment is simple and requires just a few steps.
How to Receive Money with Zelle®
Follow these steps to receive disbursements:

Ensure you’re enrolled with Zelle®. If not, visit enroll.zellepay.com to sign up.
Confirm the email or U.S. mobile number you used to enroll with Zelle®. Check with your bank if unsure.
Provide your enrolled email or U.S. mobile number to the organization sending the payment. This links the payment to your selected bank account.
When money is sent, you’ll receive a notification via email or text, confirming the funds are on their way.

Frequently Asked Questions (FAQs)
What if I accidentally deleted the email or text message telling me to enroll with Zelle®?
Visit enroll.zellepay.com to enroll using the same email or U.S. mobile number the payment notification was sent to.
Who do I call for help?
Contact the customer support team of the organization that sent the payment for assistance with payment status or issues.
Historical Context
Zelle® is the successor to clearXchange, a payment platform previously used for disbursements from companies or government entities.

Project Overview: Inbound Notification Services with Zelle®
Project Details
Project Number and Name: PR24044557 - Inbound Notification Services from EWS
Purpose: This project supports inbound notification services from the EWS Gateway, processing notifications and sending responses to the Banking Team.
Components Involved: EWS Gateway, CXC Processor WinService, Event Hub Processor WinService.
Services Consumed for Inbound Notifications
OnTokenStatusChange
OnNewPayment
OnNewPaymentRequest
OnPaymentRequestChange
OnPaymentStatusChange
DebitNetworkTransactionDetail
OnContactMethodWarning
Enhancement of OnNewPayment Notification (Release 2503D)
This release introduces the following changes to the OnNewPayment Notification:

Support for OnNewPayment Notification 4.8 with and without Zelle Risk Score.
OnNewPayment Notification 4.8 Voltage Changes.
Multi-version handling of OnNewPayment Notification (versions 4.2 and 4.8).
Uninstallation of IBM MQ 9.1 in production for CXC Processor WinService and Event Hub Processor WinService servers.
Changes Overview
Change Number	Description	Development Team
1	OnNewPayment Notification 4.8	NOW-Aztecs
2	OnNewPayment Notification 4.8 Voltage Changes	NOW-Aztecs
3	OnNewPayment Notification 4.8 and 4.2 Multiversion Support	NOW-Aztecs
4	MQ 9.1 Uninstall in CXC Processor and Event Hub WinService	NOW-Aztecs
Test Scope and Traceability
Organizational Business Lines Impacted
The following business lines are impacted by the OnNewPayment Notification enhancements:

CXC Processor WinService
Event Hub Processor WinService
Zelle Inbound Notification Events and Services
IBM MQ Services for Message Management in Queue
The goal is to validate that OnNewPayment Notification messages are processed correctly by both the CXC Processor WinService and Event Hub Processor WinService.

Test Scope Overview
The test scope focuses on validating:

Happy path flows for OnNewPayment Notification messages.
Backward compatibility between versions 4.2 and 4.8.
System integrity after voltage changes.
Successful uninstallation of IBM MQ 9.1 Messaging Service in production.
Test Cases
Happy Path Flow for OnNewPayment Notification 4.8 Without Zelle Risk Score
Happy Path Flow for OnNewPayment Notification 4.8 With Zelle Risk Score
Backward Compatibility for OnNewPayment Notification 4.2 and 4.8
Integrity Check for Voltage Changes
Uninstallation of IBM MQ 9.1 Messaging Service Application:
Ensure successful uninstallation from CXC Processor WinService and Event Hub WinService servers.
Specific Goals and Objectives
Confirm correct processing of OnNewPayment Notification 4.8 messages with and without Zelle Risk Score.
Verify seamless handling of OnNewPayment Notification versions 4.2 and 4.8.
Ensure system stability and error-free logs after voltage changes.
Validate smooth uninstallation of IBM MQ without impacting existing services.
Assumptions
All test environments are operational with proper configurations.
Test data for OnNewPayment Notification (versions 4.2 and 4.8) is available.
Access to production logs is provided for validation.
Procedures for IBM MQ uninstallation are documented.
Dependencies
Access to production environments for testing.
Availability of test tools and monitoring systems.
Dependency on teams providing production log access.
Testing Types and Applications
Test Type	Scope of Event Type	Application/Function	Manual/Automated
Functional	OnNewPayment Notification 4.8	CXC Processor WinService, Event Hub WinService	Manual
Functional	OnNewPayment Notification 4.8 Voltage Changes	CXC Processor WinService, Event Hub WinService	Manual
Functional	OnNewPayment Notification 4.8 and 4.2 Multiversion Support	CXC Processor WinService, Event Hub WinService	Manual
Functional	MQ 9.1 Uninstall in CXC Processor and Event Hub WinService	CXC Processor WinService, Event Hub WinService	Manual
Performance Testing
Overview
Performance testing was conducted for OnNewPayment Notification versions 4.2 and 4.8 on CXC Processor WinService and Event Hub WinService. Messages were dumped via the Admin Tool, and all messages were processed successfully without delays. Logs and database entries confirmed no unprocessed messages, certifying the performance testing as passed in the testing environment.

Performance Testing Details
Project #/Name	Type of Performance Testing	SLA Objective
EWS Gateway - CXC Processor WinService and Event Hub WinService	Load, Stress, Endurance, Failover	Bulk messages processed without delay, no unprocessed messages
Objective and Benefits
Confirmed that the Queue Manager can process OnNewPayment Notification 4.2 and 4.8 in the same environment.
Verified the system can handle traffic load without delays.
Test Approach
Test Methods
Test scripts and cases were created and maintained in Excel sheets.
Finalized test cases were updated in Storyboard and reviewed during Sprint closure.
Testing was conducted manually since CXC Processor WinService and Event Hub WinService are server-based applications.
The testing process was successful in the BTAT environment.
Testing Key Process Areas and Scheduling
Process Area	Start Date	End Date
Test Planning	12/24/2024	01/05/2025
Test Case Development	01/06/2025	01/26/2025
Test Environment Preparation	02/03/2025	02/28/2025
Test Data Collation	02/23/2025	02/25/2025
Test Execution	02/25/2025	02/28/2025
Test Results Analysis	02/29/2025	03/02/2025
Defect Management/Analysis	03/02/2025	03/04/2025
QA Signoff/Closure Report	03/05/2025	03/10/2025
Production Implementation	03/16/2025	03/16/2025
Test Data Management
Overview
The following test data ensures comprehensive coverage for testing the Zelle project (EWS Gateway - CXC Processor WinService and Event Hub WinService).

Test Data Samples
OnNewPayment Notification 4.2
Sample XML includes payment details such as payment ID (FE1831245650), amount ($97.89), sender (Kara Aanemone), and recipient information.
OnNewPayment Notification 4.8 With Zelle Risk Score
Sample XML includes a risk score (0.75), payment ID (FE1651658475), amount ($50.00), and attributes like days_since_profile_update and token_tenure.
OnNewPayment Notification 4.8 Without Zelle Risk Score
Sample XML includes payment ID (FE1771945650), amount ($50.00), and real-time status (true), with an empty Zelle Risk Score section.
Test Environment Preparation
Environment Details
Environment	App Server/Configuration	Support Contact	Stability	Availability
QA/BTAT A	JWCPFTKEHWS01 / JWCPFTKEHWS02	Natheen / Jamuna	100%	100%
QA/BTAT D	JWCPFTKEHWS01 / JWCPFTKEHWS02	Natheen / Jamuna	100%	100%
QA Team
Resource Name	Team	Role
Rajendran Krishnan	NOW-Aztecs	Professional
This structured format organizes the Zelle® disbursements guide and the project details
