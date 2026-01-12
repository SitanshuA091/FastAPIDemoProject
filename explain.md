### <em>WEB ARCHITECTURE</em>
**URLS and Endpoints**
- https://mywebsite.launch.com/name?video=124  
domain - https://mywebsite.launch.com  
Path/Endpoint - myname
Query parammeter - 124 after = 
- query params're seperated by & eg. - video=123&page=2
- visit interface of website is called the client/frontend
- the user interface is communicating with some api which is hosted on a server
- even signing into our account we send a req from the frontend to the backendAPI, and api returns a response
- Parts of a request component 
  - Type/method - explain below 
  - Path  - eg. https://mywebsite.launch.com/name?video=124 path/rndpoint - myname
  - Body - additional data that we want to send along with the request
  - Headers - other additional info mostly to do with authenmtication

- Response Components 
  - Status Code - eg. 404 not found indicating what happened with the request
  - Body - additional data back to send to the client side
  - Headers - security/auth type of data

  - Simple API example with Methods
    - **GET** /books - list all the books in the db
    - **DELETE** /books/{bookid} - delete the book based on their id 
    - **POST** /books - creates a book
    - **PUT** /books{bookid} - Update book based on bookid 
    - **GET** /books/{bookid} - retrieve book based on bookid 

   - some ststus codes - 404 not found, 200 Ok, 201 Created, 202 accepted, 408 req timeout

- Example Request/Response :
  - User wants to update a post they made 
  - Req Comps -
    - Type : PATCH 
    - Path : /api/post/45535  

    **Body** 
    ``` 
    {
        "title": "updated title",
        "description" : "I want to change caption"
    }
    ```
    **Headers** 
    ```
    {
        "Content type : "application/json",
        "Authorization" : "bearer ajhfgghdhhd"
    }
    ```
   - Response Components 
     - Status Code: 204

     **Body**
     ```
     {
     "title" :"updated title",
     "description" : "I want to change caption"
     "postId" : 45365
     "updatedAt" : "Sept 26, 2025"
     "createdBy" : "user123"
     }
     ```

     **Headers**
     ```
     {
        "Content-Type" : "application-json"
     }
     ```
- Authentication
  - JWT token is sent along with every request - to confirm authorization that request can be performed
