import random

# Slimmed-down XML template with fewer fields and compact format
xml_template = '<OnNewPaymentNotification4.8 xmlns="http://clearxchange.com/r4" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://clearxchange.com/r4 s.xsd"><event-id>9193447423</event-id><event-time>2024-11-07T22:22:23Z</event-time><payment><payment-id>{payment_id}</payment-id><amount currency="USD">50.00</amount><initiation-time>2024-11-07T22:22:22Z</initiation-time><sender><organization-id>FE1</organization-id><sender-id>paymentTesting</sender-id><name>payment</name><sender-type>person</sender-type><sender-fi-instrument>DDA</sender-fi-instrument><address><line1>456 gjgb dr</line1><city>dallas</city><state-or-subdivision-code>tx</state-or-subdivision-code><zip>76456</zip><country-code>USA</country-code></address></sender><product-type>p2p</product-type><directory-reference-number>CQ1123451100</directory-reference-number><real-time>true</real-time><status><sent/></status><to-known-recipient><recipient-payment-profile-id>{recipient_payment_profile_id}</recipient-payment-profile-id><recipient-organization-id>F58</recipient-organization-id><recipient-type>small-business</recipient-type><recipient-fi-instrument>DDA</recipient-fi-instrument></to-known-recipient></payment><zelle-risk-score><status>success</status><score>0.75</score></zelle-risk-score></OnNewPaymentNotification4.8>'

# Function to generate a unique payment-id
def generate_payment_id(used_ids):
    base = "FE1651684"
    while True:
        suffix = ''.join([str(random.randint(0, 9)) for _ in range(3)])  # Random 3-digit suffix
        payment_id = base + suffix
        if payment_id not in used_ids:  # Check if it's unique
            used_ids.add(payment_id)
            return payment_id

# Function to generate a unique recipient-payment-profile-id (shortened UUID)
def generate_recipient_payment_profile_id():
    # Generate a shorter UUID-like string (e.g., 8-4-4 characters)
    return f"{random.randint(10000000, 99999999)}-{random.randint(1000, 9999)}-{random.randint(1000, 9999)}"

# Generate 1000 XML messages with unique payment-ids and smaller size
used_payment_ids = set()
with open('output.xml', 'w') as file:
    for _ in range(1000):
        payment_id = generate_payment_id(used_payment_ids)
        recipient_payment_profile_id = generate_recipient_payment_profile_id()
        xml_message = xml_template.format(
            payment_id=payment_id,
            recipient_payment_profile_id=recipient_payment_profile_id
        )
        file.write(xml_message + '\n')  # Single newline, no blank line

print("1000 XML messages have been written to 'output.xml' (target size < 1 MB)")
