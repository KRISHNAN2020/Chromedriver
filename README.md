import xml.etree.ElementTree as ET
import random
import string
import uuid
from datetime import datetime, timedelta

def generate_payment_id():
    """Generate payment ID like FE1651684482 with FE1 constant"""
    middle = random.randint(651, 999)  # Random 3 digits between 651 and 999
    last = random.randint(684482, 999999)  # Random 6 digits
    return f"FE1{middle}{last}"

def generate_directory_ref():
    """Generate directory reference like CQ1123451100"""
    digits = ''.join(random.choices(string.digits, k=8))
    return f"CQ11{digits}"

def generate_recipient_profile_id():
    """Generate UUID-like string in format e6b167c2-a5cd-36ad-9dbf-03dc20d82c7c"""
    return str(uuid.uuid4()).replace('-', '')[:32]

def generate_event_time():
    """Generate timestamp like 2024-11-07T22:22:23.062Z"""
    base_date = datetime(2024, 11, 7, 22, 22, 23)
    random_seconds = random.randint(0, 86400)  # Random seconds in a day
    new_time = base_date + timedelta(seconds=random_seconds)
    return new_time.strftime("%Y-%m-%dT%H:%M:%S.062Z")

def generate_event_id():
    """Generate event ID like 9193447423"""
    return ''.join(random.choices(string.digits, k=10))

def create_payment_xml(output_filename="payment_notifications.xml"):
    print("Starting XML file creation process...")
    
    with open(output_filename, 'w', encoding='utf-8') as f:
        f.write('<?xml version="1.0" encoding="utf-8"?>\n')
        f.write('<PaymentNotifications>\n')
        print("Created root element: PaymentNotifications")
        
        for i in range(1000):
            notification = ET.Element("OnNewPaymentNotification4.8")
            notification.set("xmlns", "http://clearxchange.com/release4_0")
            notification.set("xmlns:xsi", "http://www.w3.org/2001/XMLSchema-instance")
            notification.set("xsi:schemaLocation", "http://clearxchange.com/release4_0 sd-schema4_0.xsd")
            
            # Event details with random values
            event_id = ET.SubElement(notification, "event-id")
            event_id.text = generate_event_id()
            
            event_time = ET.SubElement(notification, "event-time")
            event_time.text = generate_event_time()
            
            # Payment details
            payment = ET.SubElement(notification, "payment")
            
            payment_id = ET.SubElement(payment, "payment-id")
            payment_id.text = generate_payment_id()
            
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
            dir_ref.text = generate_directory_ref()
            
            real_time = ET.SubElement(payment, "real-time")
            real_time.text = "true"
            
            disburser = ET.SubElement(payment, "disburser-details")
            
            status = ET.SubElement(payment, "status")
            sent = ET.SubElement(status, "sent")
            
            # Recipient
            recipient = ET.SubElement(payment, "to-known-recipient")
            recip_profile = ET.SubElement(recipient, "recipient-payment-profile-id")
            recip_profile.text = generate_recipient_profile_id()
            
            recip_org = ET.SubElement(recipient, "recipient-organization-id")
            recip_org.text = "F58"
            
            recip_type = ET.SubElement(recipient, "recipient-type")
            recip_type.text = "small-business"
            
            recip_fi = ET.SubElement(recipient, "recipient-fi-instrument")
            recip_fi.text = "DDA"
            
            # Zelle score
            zelle_score = ET.SubElement(notification, "zelle-risk-score")
            
            # Write single-line message
            message = ET.tostring(notification, encoding='unicode', method='xml')
            message = message.replace('\n', '').replace('\r', '')
            f.write(message + '\n')
            
            print(f"Message {i+1}: {message}")
            if (i + 1) % 100 == 0:
                print(f"Processed {i + 1} payment notifications")
        
        f.write('</PaymentNotifications>\n')
        print(f"XML file successfully created as '{output_filename}' with 1000 payment notifications")
    
    print("Process completed!")

if __name__ == "__main__":
    create_payment_xml()
