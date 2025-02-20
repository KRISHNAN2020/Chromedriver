import re

# Function to extract timestamp from a string
def extract_timestamp(json_content):
    # Regex pattern to match timestamp up to milliseconds
    pattern = r'"time":"(\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}\.\d{3})'
    timestamps = re.findall(pattern, json_content)  # Find all matches
    return timestamps

# Input and output file paths
input_json_file = r"C:\Python\UnformattedText.json"  
# Replace with your JSON file path"
output_txt_file = r"C:\Python\Result.json'  # Output file for timestamps"

# Read the JSON file
try:
    with open(input_json_file, 'r', encoding='utf-8') as file:
        json_content = file.read()

    # Extract all timestamps
    timestamps = extract_timestamp(json_content)

    # Write timestamps to a new text file
    if timestamps:
        with open(output_txt_file, 'w', encoding='utf-8') as output_file:
            for timestamp in timestamps:
                output_file.write(timestamp + '\n')  # Write each timestamp on a new line
        print(f"Extracted {len(timestamps)} timestamps and saved to '{output_txt_file}'")
    else:
        print("No timestamps found in the JSON file.")
        
except FileNotFoundError:
    print(f"Error: The file '{input_json_file}' was not found.")
except Exception as e:
    print(f"An error occurred: {str(e)}")
