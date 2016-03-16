---
layout: page
title: Authentication
category: rfc
status: done
---

Authentication for an user is done using a POST with it's username and password
on /authentications REST API. Response from this API contain user ID (uuid) and
it's current access token.

Then call to authenticated API is done using normal HTTP authentication mechanism,
using an Authorization header, with user_id as username and access_token as password


```python
    import requests
    from requests.auth import HTTPBasicAuth

    authentication = {
        'username': 'julien.muetton@gandi.net',
        'password': '123456'
        }

    base_url = 'http://127.0.0.1:6543'

    res = requests.post('%s/api/authentications' % base_url, data=authentication)
    data = res.json()
    print(data)
    {
        "username": "julien.muetton@gandi.net",
        "tokens": {
            "access_token": "31882962150c107b8a1ed9f1d1605d0febe5953f",
            "expires_in": 3600,
            "refresh_token": "25ba837ba17f13a8b7e2b76f6c5a308de0d90b410fd06337b7cab52ae1e7d072738ee7df3564de1f"},
        "user_id": "2f1faadb-9032-42df-a0fe-9331e619b40c"
    }

    auth = HTTPBasicAuth(data['user_id'], data['tokens']['access_token'])
    requests.get('%s/api/threads' % base_url, auth=auth)
```
