---
layout: post
title: Weather API Classwork
subtitle: Pull Information from Web API
tags: [homework]
comments: true
---



# Code



```python

import requests

url = "http://api.weatherapi.com/v1/current.json"
key = "90bd28c642494cb5b9c133754202011"

payload1 = {
    'key': key,
    'q': "San Francisco"
}
payload2 = {
    'key': key,
    'q': "Guangzhou"
}
payload3 = {
    'key': key,
    'q': "-0.33237,8.08318"
}
payload4 = {
    'key': key,
    'q': "53.216.147.194"
}

payload = []
payload.append(payload1)
payload.append(payload2)
payload.append(payload3)
payload.append(payload4)

for i in range(0,4):
    response = requests.get(url, params=payload[i])
    if response.status_code == 200:
        data = response.json()
        print(data['current']['wind_dir'])
    else:
        print("Error!!!")

```