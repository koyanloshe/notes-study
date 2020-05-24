# API Design

*200 OK *

The request has succeeded. 
*
*
*201 Created *

The request has been fulfilled and resulted in a new resource being created. 
*
*
*202 Accepted *

The request has been accepted for processing, but the process‐ ing has not been completed. 
*
*
*204 No Content *

The server has fulfilled the request but does not need to return a body. This is common for delete operations. 
*
*
*400 Bad Request *

The request could not be understood by the server due to mal‐ formed syntax. 
*
*
*401 Unauthorized *

The request requires user authentication. 
*
*
*403 Forbidden *

The server understood the request, but is refusing to fulfill it. 
*
*
*404 Not Found *

The server has not found anything matching the requested URI. 
*
*
*500 Internal Server Error *

The server encountered an unexpected condition which preven‐ ted it from fulfilling the request. 

## API type:

|  “List”, “Search”, “Match”, “View All”  | GET collection |
|-----|-----|
|  “Show”, “Retrieve”, “View”  | GET resource instance |
|  
 | POST create a new resource |
|  “Replace”  | PUT update a resource collection |
|  “Update” | PUT update a resource instance |
|  “Delete All”, “Remove All”, “Clear”, “Reset” | DELETE delete a resource collection  |
|  “Delete”, “Remove” | DELETE delete a resource instance |
|  <other verbs>  | POST custom action on a resource instance  |

## HTTP codes

![API Design-1](images/API%20Design-1.tiff)

