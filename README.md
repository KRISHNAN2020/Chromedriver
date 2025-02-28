import xml.etree.ElementTree as ET
import random
import string

def generate_unique_id(prefix, length=10):
    """Generate a unique ID with a prefix"""
    random_digits = ''.join(random.choices(string.digits, k=length))
    return f"{prefix}{random_digits}"

def create_payment_xml(output_filename="payment_notifications.xml"):
    print("Starting XML file creation process...")
    
    # Open file for writing
    with open(output_filename, 'w', encoding='utf-8') as f:
        # Write XML declaration and root opening
        f.write('<?xml version="1.0" encoding="utf-8"?>\n')
        f.write('<PaymentNotifications>\n')
        print("Created root element: PaymentNotifications")
        
        # Generate 1000 messages
        for i in range(1000):
            # Create notification element
            notification = ET.Element("OnNewPaymentNotification4.8")
            notification.set("xmlns", "http://clearxchange.com/release4_0")
            notification.set("xmlns:xsi", "http://www.w3.org/2001/XMLSchema-instance")
            notification.set("xsi:schemaLocation", "http://clearxchange.com/release4_0 sd-schema4_0.xsd")
            
            # Event details
            event_id = ET.SubElement(notification, "event-id")
            event_id.text = "9193447423"
            
            event_time = ET.SubElement(notification, "event-time")
            event_time.text = "2024-11-07T22:22:23.062Z"
            
            # Payment details
            payment = ET.SubElement(notification, "payment")
            
            payment_id = ET.SubElement(payment, "payment-id")
            payment_id.text = generate_unique_id("PM")
            
            amount = ET.SubElement(payment, "amount")
            amount.set("currency", "USD")
            amount.text = "50.00"
            
            initiation_time = ET.SubElement(payment, "initiation-time")
            initiation_time.text = "2024-11-07T22:22:22.808Z"
            
            # Sender details
            sender = ET.SubElement(payment, "sender")
            
            org_id = ET.SubElement(sender, "organization-id")
            org_id.text = "FE1"
            
            sender_id = ET.SubElement(sender, "sender-id")
            sender_id.text = "paymentTesting"
            
            name = ET.SubElement(sender, "name")
            name.text = "payment"
            
            sender_type = ET.SubElement(sender, "sender-type")
            sender_type.text = "person"
            
            sender_fi = ET.SubElement(sender, "sender-fi-instrument")
            sender_fi.text = "DDA"
            
            # Address
            address = ET.SubElement(sender, "address")
            line1 = ET.SubElement(address, "line1")
            line1.text = "456 gjgb dr"
            line2 = ET.SubElement(address, "line2")
            line2.text = "456 gjgb dr"
            city = ET.SubElement(address, "city")
            city.text = "dallas"
            state = ET.SubElement(address, "state-or-subdivision-code")
            state.text = "tx"
            zip_code = ET.SubElement(address, "zip")
            zip_code.text = "76456"
            country = ET.SubElement(address, "country-code")
            country.text = "USA"
            
            # Other payment details
            product_type = ET.SubElement(payment, "product-type")
            product_type.text = "p2p"
            
            dir_ref = ET.SubElement(payment, "directory-reference-number")
            dir_ref.text = "CQ1123451100"
            
            real_time = ET.SubElement(payment, "real-time")
            real_time.text = "true"
            
            disburser = ET.SubElement(payment, "disburser-details")
            
            status = ET.SubElement(payment, "status")
            sent = ET.SubElement(status, "sent")
            
            # Recipient
            recipient = ET.SubElement(payment, "to-known-recipient")
            recip_profile = ET.SubElement(recipient, "recipient-payment-profile-id")
            recip_profile.text = generate_unique_id("RP")
            
            recip_org = ET.SubElement(recipient, "recipient-organization-id")
            recip_org.text = "F58"
            
            recip_type = ET.SubElement(recipient, "recipient-type")
            recip_type.text = "small-business"
            
            recip_fi = ET.SubElement(recipient, "recipient-fi-instrument")
            recip_fi.text = "DDA"
            
            # Zelle score
            zelle_score = ET.SubElement(notification, "zelle-risk-score")
            
            # Convert to single-line string
            message = ET.tostring(notification, encoding='unicode', method='xml')
            message = message.replace('\n', '').replace('\r', '')
            
            # Write to file (single line per message)
            f.write(message + '\n')
            
            # Print to console
            print(f"Message {i+1}: {message}")
            
            if (i + 1) % 100 == 0:
                print(f"Processed {i + 1} payment notifications")
        
        # Write closing tag
        f.write('</PaymentNotifications>\n')
        print(f"XML file successfully created as '{output_filename}' with 1000 payment notifications")
    
    print("Process completed!")

if __name__ == "__main__":
    create_payment_xml()
