import re

# List of patterns to look for
PATTERNS = {
    "Google API Key": r"AIza[0-9A-Za-z\\-_]{35}",
    "Generic Secret": r"(?i)(secret|password|passwd|api_key|access_token) *= *['\"]?[a-zA-Z0-9]{8,}['\"]?"
}

def scan_text(content):
    found_secrets = []
    for name, pattern in PATTERNS.items():
        if re.search(pattern, content):
            found_secrets.append(name)
    return found_secrets

# Test it
test_code = 'api_key = "AIzaSyAs7exampleKey1234567890abcdefgh"'
print(f"Detected: {scan_text(test_code)}")
