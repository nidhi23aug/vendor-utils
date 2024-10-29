# Authentication

**Description**: Before accessing data from the Planet API, authenticate using your API key. This step is essential for verifying permissions to access Planet’s datasets.

- **Input**: Planet API Key
- **Expected Output**: Successful login message or an error if authentication fails.

**Code Snippet**:
```python
import os
from planet import Auth

# Authenticate with Planet API key
api_key = os.getenv("PL_API_KEY")
auth = Auth.from_key(api_key)
print("Authenticated successfully!")
