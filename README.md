import uuid
import random
from datetime import datetime

# Base XML template with placeholders for dynamic values
xml_template = '''<OnNewPaymentNotification4.8 xmlns="http://clearxchange.com/release4_0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://clearxchange.com/release4_0 sd-schema4_0.xsd"><event-id>9193447423</event-id><event-time>2024-11-07T22:22:23.062Z</event-time><payment><payment-id>{payment_id}</payment-id><amount currency="USD">50.00</amount><initiation-time>2024-11-07T22:22:22.808Z</initiation-time><sender><organization-id>FE1</organization-id><sender-id>paymentTesting</sender-id><name>payment</name><sender-type>person</sender-type><sender-fi-instrument>DDA</sender-fi-instrument><address><line1>456 gjgb dr</line1><line2>456 gjgb dr</line2><city>dallas</city><state-or-subdivision-code>tx</state-or-subdivision-code><zip>76456</zip><country-code>USA</country-code></address></sender><product-type>p2p</product-type><directory-reference-number>CQ1123451100</directory-reference-number><real-time>true</real-time><disburser-details/><status><sent/></status><to-known-recipient><recipient-payment-profile-id>{recipient_payment_profile_id}</recipient-payment-profile-id><recipient-organization-id>F58</recipient-organization-id><recipient-type>small-business</recipient-type><recipient-fi-instrument>DDA</recipient-fi-instrument></to-known-recipient></payment><zelle-risk-score><status>success</status><status-code>0</status-code><model><identifier>6000001</identifier><score>0.75</score><reason-code><key>reason1</key><value>no reason</value></reason-code><attribute><key>days_since_profile_update</key><value>-1</value></attribute><attribute><key>link_tkn_to_recip_acct_1d</key><value>0</value></attribute><attribute><key>link_tkn_to_recip_acct_3d</key><value>0</value></attribute><attribute><key>link_tkn_to_recip_acct_7d</key><value>0</value></attribute><attribute><key>nl_email_domain_match</key><value>0</value></attribute><attribute><key>r_token_flips_1d</key><value>0</value></attribute><attribute><key>r_token_flips_30d</key><value>0</value></attribute><attribute><key>r_token_flips_7d</key><value>0</value></attribute><attribute><key>rcomb_avg_trx_14d</key><value>0.00</value></attribute><attribute><key>rcomb_cnt_1d</key><value>0</value></attribute><attribute><key>rcomb_dsnc_first_pay</key><value>0</value></attribute><attribute><key>rcomb_rat_avg3d_7d</key><value>-327.67</value></attribute><attribute><key>rr_amt_14d</key><value>0.00</value></attribute><attribute><key>rr_amt_7d</key><value>0.00</value></attribute><attribute><key>rr_amt_max_12h</key><value>0.00</value></attribute><attribute><key>rr_amt_max_1d</key><value>0.00</value></attribute><attribute><key>rr_amt_max_30d</key><value>0.00</value></attribute><attribute><key>rr_amt_min_60d</key><value>0.00</value></attribute><attribute><key>rr_rat_cnt3d_7d</key><value>-1.27</value></attribute><attribute><key>rr_unq_senders_1d</key><value>0</value></attribute><attribute><key>rr_unq_senders_30d</key><value>0</value></attribute><attribute><key>rr_unq_senders_7d</key><value>0</value></attribute><attribute><key>rr_unq_senders_90d</key><value>0</value></attribute><attribute><key>token_org_tenure</key><value>0.00</value></attribute><attribute><key>token_status_changes_30d</key><value>0</value></attribute><attribute><key>token_tenure</key><value>-1.00</value></attribute><attribute><key>zfc_ato_3rdpty_recv_90d</key><value>0</value></attribute><attribute><key>zfc_flag</key><value>0</value></attribute><attribute><key>zfc_scam_recv_90d</key><value>0</value></attribute><status-code>0</status-code></model></zelle-risk-score></OnNewPaymentNotification4.8>'''

# Function to generate a unique payment-id
def generate_payment_id(used_ids):
    base = "FE1651684"
    while True:
        suffix = ''.join([str(random.randint(0, 9)) for _ in range(3)])  # Random 3-digit suffix
        payment_id = base + suffix
        if payment_id not in used_ids:  # Check if it's unique
            used_ids.add(payment_id)
            return payment_id

# Function to generate a unique recipient-payment-profile-id (UUID-like)
def generate_recipient_payment_profile_id():
    base_uuid = "e6b5528b-a5cd-4342-9dbf-03dc20d82c7c"
    parts = base_uuid.split('-')
    # Modify the first part randomly
    parts[0] = "e6b" + ''.join([random.choice('0123456789abcdef') for _ in range(5)])
    # Modify the third part randomly
    parts[2] = ''.join([random.choice('0123456789abcdef') for _ in range(4)])
    return '-'.join(parts)

# Generate 1000 XML messages with unique payment-ids
used_payment_ids = set()  # Set to track used payment-ids
with open('output.xml', 'w') as file:
    for _ in range(1000):
        payment_id = generate_payment_id(used_payment_ids)
        recipient_payment_profile_id = generate_recipient_payment_profile_id()
        xml_message = xml_template.format(
            payment_id=payment_id,
            recipient_payment_profile_id=recipient_payment_profile_id
        )
        file.write(xml_message + '\n')  # Single newline, no blank line

print("1000 XML messages with unique payment-ids have been written to 'output.xml'")
