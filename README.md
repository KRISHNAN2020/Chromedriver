import random
import string
from datetime import datetime

def generate_unique_id(prefix, length=10):
    """Generate a unique ID with a prefix"""
    random_digits = ''.join(random.choices(string.digits, k=length))
    return f"{prefix}{random_digits}"

def create_payment_xml(output_filename="payment_notifications.xml"):
    # Print initial message
    print("Starting XML file creation process...")
    
    # Single-line message template
    message_template = '<OnNewPaymentNotification4.8 xmlns="http://clearxchange.com/release4_0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://clearxchange.com/release4_0 sd-schema4_0.xsd"><event-id>9193447423</event-id><event-time>2024-11-07T22:22:23.062Z</event-time><payment><payment-id>{payment_id}</payment-id><amount currency="USD">50.00</amount><initiation-time>2024-11-07T22:22:22.808Z</initiation-time><sender><organization-id>FE1</organization-id><sender-id>paymentTesting</sender-id><name>payment</name><sender-type>person</sender-type><sender-fi-instrument>DDA</sender-fi-instrument><address><line1>456 gjgb dr</line1><line2>456 gjgb dr</line2><city>dallas</city><state-or-subdivision-code>tx</state-or-subdivision-code><zip>76456</zip><country-code>USA</country-code></address></sender><product-type>p2p</product-type><directory-reference-number>CQ1123451100</directory-reference-number><real-time>true</real-time><disburser-details/><status><sent/></status><to-known-recipient><recipient-payment-profile-id>{recipient_payment_profile_id}</recipient-payment-profile-id><recipient-organization-id>F58</recipient-organization-id><recipient-type>small-business</recipient-type><recipient-fi-instrument>DDA</recipient-fi-instrument></to-known-recipient></payment><zelle-risk-score/></OnNewPaymentNotification4.8>'
    
    # Open file for writing
    with open(output_filename, 'w', encoding='utf-8') as f:
        # Write XML declaration and root opening tag
        f.write('<?xml version="1.0" encoding="utf-8"?>\n')
        f.write('<PaymentNotifications>\n')
        print("Created root element: PaymentNotifications")
        
        # Generate 1000 messages
        for i in range(1000):
            # Generate unique IDs
            payment_id = generate_unique_id("PM")
            recipient_profile_id = generate_unique_id("RP")
            
            # Format the message
            message = message_template.format(
                payment_id=payment_id,
                recipient_payment_profile_id=recipient_profile_id
            )
            
            # Write formatted message with indentation
            indented_message = "    " + "\n    ".join(message.split(">"))
            f.write(indented_message + "\n")
            
            # Print the single-line version
            print(f"Message {i+1}: {message}")
            
            # Progress update every 100 records
            if (i + 1) % 100 == 0:
                print(f"Processed {i + 1} payment notifications")
        
        # Write closing root tag
        f.write('</PaymentNotifications>\n')
        print(f"XML file successfully created as '{output_filename}' with 1000 payment notifications")
    
    # Print completion message
    print("Process completed!")

# Execute the function
if __name__ == "__main__":
    create_payment_xml()
