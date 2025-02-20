import re
import json

def extract_timestamp(json_content: str) -> str:
    """
    Extract the timestamp from the 'raw' field in JSON content.
    Returns the timestamp as a string in the format 'YYYY-MM-DD HH:MM:SS,sss [nn]'.
    """
    timestamp = None
    
    # Try parsing with JSON first
    try:
        data = json.loads(json_content)
        if 'result' in data and 'raw' in data['result']:
            raw_value = data['result']['raw']
            # Extract timestamp using regex from the raw string
            match = re.match(r'(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2},\d{3} \[\d+\])', raw_value)
            if match:
                timestamp = match.group(1)
    except json.JSONDecodeError:
        print("JSON decoding failed, falling back to regex extraction...")
        # Regex to extract timestamp directly from the raw field
        pattern = r'"raw":"(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2},\d{3} \[\d+\])'
        match = re.search(pattern, json_content)
        if match:
            timestamp = match.group(1)
    
    return timestamp

def process_json_text(json_text: str):
    """
    Process JSON text, extract timestamp, and print to console.
    """
    # Split into individual JSON objects if multiple are present (newline-separated)
    json_objects = json_text.strip().split('\n')
    timestamps = []

    # Process each JSON object
    for obj in json_objects:
        if obj.strip():  # Skip empty lines
            timestamp = extract_timestamp(obj)
            if timestamp:
                timestamps.append(timestamp)

    # Print timestamps to console
    if timestamps:
        print("Extracted timestamps:")
        for i, ts in enumerate(timestamps, 1):
            print(f"{i}. {ts}")
        print(f"Total timestamps extracted: {len(timestamps)}")
    else:
        print("No timestamps extracted.")

# The JSON text provided
json_text = ''' '''

# Run the processing function
process_json_text(json_text)
