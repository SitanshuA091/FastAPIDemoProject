# **FASTAPI** IMPORTANT NOTES
- **Fast application programming interface**,backend framework. runs on server and essesntially controls data.
- `app.get("/")` - this creates an API which has one endpoint / and returns a json output with the function returns 
- to run this APi we run `uvicorn main:app --reload`.
### Path Parameters
- path params are params in the path of a url. they are defined using braces `{}`eg.- an API with a path param for a person's name  
```python
@app.get("/greet/{name}")
def welcome(name: str):
    return f"Hello {name}"
```
- so calling `/welcome/john` will translate to `Hello John` as name = "John".
### Query Parameters
- Query parameters are key-value pairs in the query string of a URL `/items?category=sport&sportname=cricket`
- they can be declared like this - 
```python
@app.get("/items/")
def read_items(category: str, sportname: str)
   ...
```
when we call `/items?category=sport&sportname=cricket`, FastAPI will validate the params and pass to the function `read_items`: category = "sports", sportname = "cricket"
- the types for the query params are defined using python hints, FastAPI uses pydantic to validate the params and serialize them to declared types.
### Request Body
- Request Body contains data in a request, eg. in a POST request, we can declare a req. body in FastAPI
```python
from pydantic import BaseModel 
class Item(BaseModel):
    name: str,
    description: str, 
    price: float

@app.post("/items/")
def create_item(item: Item):
    ....
```
- An Item model is defined using Pydantic. In the path operation, this model validates and serialize the req. body when item is called.
### Response Model
- A model can be decalred for API response and FastAPI converts it into JSOn.
- In the read items function - 
```Python
@app.get("/items/")
def read_items():
items = [
        { "name": "Foo", "description": "A new item", "price": 45.2 },
        { "name": "Bar", "description": "Another item", "price": 10.5 }
    ]
    return items  
```
Response will be 
```
[
    {
        "name": "Foo",
        "description": "A new item",
        "price": 45.2
    },
    {
        "name": "Bar", 
        "description": "Another item",
        "price": 10.5 
    }
]
```