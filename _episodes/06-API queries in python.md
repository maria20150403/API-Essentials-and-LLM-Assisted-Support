---
title: "API queries in python"
teaching: 15
exercises: 5
questions:
- "What is the difference between authentication and authorization?"
- "What are API keys?"
- "How do we obtain an API key?"
objectives:
- "Understand the purpose of authentication and authorisation."
- "Understand the different methods of authentication."
- "Be able to obtain and use an API key to access data."
keypoints:
- "Authentication ensures that only authorised entities can access the API."
- "Authorisation ensures they can only access what they're permitted to."
---


### Essential Libraries

- **`requests`**:
The requests library in Python is a popular and user-friendly HTTP library that simplifies the process of making HTTP requests. It abstracts away much of the complexity involved in sending HTTP requests and handling responses.
The requests.get function is used to send a GET request to a specified URL.

- **`json`**:
One of the primary uses of the `json` module is to parse JSON data received from an API into Python dictionaries, allowing for easy access and manipulation of the data within a Python program. JSON is easy for humans to read and write and easy for machines to parse and generate.

- `json.loads()`: This function is used to parse a JSON string, converting it into a Python dictionary. `loads` stands for "load string."

#### Example of Parsing JSON:

```python
import json

# Sample JSON data received from an API
json_data = '{"name": "John", "age": 30, "city": "New York"}'

# Parse JSON data into a Python dictionary
data_dict = json.loads(json_data)

print(data_dict)  # Output: {'name': 'John', 'age': 30, 'city': 'New York'}
```

### Formatting the Output

- **`json.dumps`**:
The `json.dumps()` function provides parameters like `indent` and `sort_keys` to format the JSON output, making it more readable. This function takes a Python object (like a dictionary) and returns a JSON string.


#### Example of Converting to JSON:

```python
import json

# A Python dictionary
data_dict = {
    "name": "Jane",
    "age": 25,
    "city": "Los Angeles"
}

# Convert the Python dictionary to a JSON string

json_data = json.dumps(data_dict,indent=4, sort_keys=True)

print(json_data)  # Output: '{"name": "Jane", "age": 25, "city": "Los Angeles"}'
```
## API keys

Using environment variables to store API keys is a safer alternative that keeps sensitive information like API keys out of your source code, making your application more secure. 

### Setting the Environment Variable

First, you'll need to set the environment variable in your operating system.

#### On Windows:

1. Open the Start Search, type in "env", and choose "Edit the system environment variables."
2. In the System Properties window, click on the "Environment Variables…" button.
3. In the Environment Variables window, click on the "New…" button under the "User variables" section.
4. Set the variable name as `NASA_API_KEY` and its value to your actual NASA API key.

#### On macOS/Linux:

1. Open your terminal.
2. Use the `export` command to set an environment variable. Add this line to your `~/.bashrc`, `~/.zshrc`, or `~/.profile` file to make it persistent across sessions:

   ```bash
   export NASA_API_KEY='your_nasa_api_key_here'
   ```

3. After adding the line, run `source ~/.bashrc`, `source ~/.zshrc`, or `source ~/.profile` to reload the configuration and apply the changes.

### Step 2: Accessing the Environment Variable in Python

Now, in your Python script, use the `os` module to access the environment variable:

```python
import requests
import os

base_url = "https://api.nasa.gov"
endpoint = f"{base_url}/planetary/apod/"
headers = {"accept": "application/json"}

# Access the API key from environment variables
api_key = os.getenv("NASA_API_KEY")

if not api_key:
    raise ValueError("No API Key found. Please set the NASA_API_KEY environment variable.")

params = {"api_key": api_key, "count": 2}

response = requests.get(endpoint, params=params, headers=headers)
print(response.json())
```

