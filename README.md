import random
import string
from datetime import datetime, timedelta

# XML template with placeholders for dynamic values
xml_template = '<?xml version="1.0" encoding="UTF-8"?><OnContactMethodWarningNotification4.3 xmlns="http://clearxchange.com/release4_0"><event-id>{event_id}</event-id><event-time>{event_time}</event-time><token><normalized-value>{normalized_value}</normalized-value><type>zelletag</type><status>active</status></token><associated-contact-method>{associated_contact_method}</associated-contact-method><warning-reason>carrier-disconnect</warning-reason></OnContactMethodWarningNotification4.3>'

# Function to generate a unique event-id (6-digit number)
def generate_event_id(used_ids):
    while True:
        event_id = str(random.randint(100000, 999999))  # 6-digit number
        if event_id not in used_ids:
            used_ids.add(event_id)
            return event_id

# Function to generate a unique event-time (timestamp with millisecond precision)
def generate_event_time(used_times):
    base_time = datetime(2024, 6, 20, 9, 53, 38)  # Starting point from example
    while True:
        # Add random seconds and milliseconds
        delta_seconds = random.randint(0, 86400)  # Up to 1 day variation
        delta_millis = random.randint(0, 999)     # Milliseconds 000-999
        event_time = base_time + timedelta(seconds=delta_seconds, milliseconds=delta_millis)
        event_time_str = event_time.strftime('%Y-%m-%dT%H:%M:%S.%f')[:-3] + 'Z'  # Format with 3-digit millis
        if event_time_str not in used_times:
            used_times.add(event_time_str)
            return event_time_str

# Function to generate a unique normalized-value (8-character alphanumeric string)
def generate_normalized_value(used_values):
    while True:
        normalized_value = ''.join(random.choices(string.ascii_lowercase + string.digits, k=8))
        if normalized_value not in used_values:
            used_values.add(normalized_value)
            return normalized_value

# Function to generate a unique associated-contact-method (10-digit phone number)
def generate_associated_contact_method(used_numbers):
    while True:
        contact_method = ''.join([str(random.randint(2, 9)) if i == 0 else str(random.randint(0, 9)) for i in range(10)])  # 10-digit, no leading 0 or 1
        if contact_method not in used_numbers:
            used_numbers.add(contact_method)
            return contact_method

# Generate 1000 XML messages with unique values
used_event_ids = set()
used_event_times = set()
used_normalized_values = set()
used_contact_methods = set()

with open('output.txt', 'w') as file:
    for _ in range(1000):
        event_id = generate_event_id(used_event_ids)
        event_time = generate_event_time(used_event_times)
        normalized_value = generate_normalized_value(used_normalized_values)
        associated_contact_method = generate_associated_contact_method(used_contact_methods)
        
        xml_message = xml_template.format(
            event_id=event_id,
            event_time=event_time,
            normalized_value=normalized_value,
            associated_contact_method=associated_contact_method
        )
        file.write(xml_message + '\n')  # Single newline, no blank line

print("1000 unique XML messages have been written to 'output.txt'")
