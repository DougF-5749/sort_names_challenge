
# {{ NAME }} Route Design Recipe

# Request:
POST http://localhost:5001/sort-names

# With body parameters:
names=Joe,Alice,Zoe,Julia,Kieran

# Expected response (sorted list of names):
Alice,Joe,Julia,Kieran,Zoe

## 1. Design the Route Signature

_Include the HTTP method, the path, and any query or body parameters._

```
# Home route
POST /sort-names

# sort-names message route
POST /sort-names
  names: comma-separated string
```

## 2. Create Examples as Tests

_Go through each route and write down one or more example responses._

_Remember to try out different parameter values._

_Include the status code and the response body._

```python

"""
# POST /sort-names
data={'names': 'Joe,Alice,Zoe,Julia,Kieran'}
#  Expected response (200 OK):
#  Alice,Joe,Julia,Kieran,Zoe
"""

"""
# POST /sort-names
data={'names': 'Joe,Zlice,Zoe,Julia,Kieran'}
#  Expected response (200 OK):
#  Joe,Julia,Kieran,Zoe,Zlice
"""
```

## 3. Test-drive the Route

_After each test you write, follow the test-driving process of red, green, refactor to implement the behaviour._

Here's an example for you to start with:

```python
"""
POST /sort-names
  Expected response (200 OK):
  "This is my sort-names page!"
"""
def test_POST_sort-names(web_client):
    response = web_client.POST('/sort-names')
    assert response.status_code == 200
    assert response.data.decode('utf-8') == 'This is my sort-names page!'

