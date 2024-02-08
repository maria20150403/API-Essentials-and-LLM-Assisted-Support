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

~~~
import requests
import json

base_url = "https://api.nasa.gov"#/planetary/apod?api_key=DEMO_KEY&count=1"
endpoint = f"{base_url}/planetary/apod/"
headers = {"accept": "application/json"}
params = {"api_key": "DEMO_KEY", "count": 1}

#response = requests.get("https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY")#,headers=headers)
response = requests.get(endpoint,params=params, headers=headers)
#print(response.json())
print(json.dumps(response.json(),indent=4, sort_keys=True))
~~~
{: .python}