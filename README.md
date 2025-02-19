import re

# The JSON string you provided, but simplified for regex extraction
json_string = ''' '''

# Use regex to find and extract the timestamp, limiting to milliseconds
timestamp_match = re.search(r'"time":"(\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}\.\d{3})', json_string)

if timestamp_match:
    # Group 1 in the regex match contains the timestamp up to milliseconds
    print(timestamp_match.group(1))
else:
    print("Timestamp not found.")
