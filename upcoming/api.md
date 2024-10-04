# API

what are some of the best practices in API design.

For our purposes I am working exclusively with RESTful APIs.
- clarify what exactly that means
- what are some of the alternatives
- does graphQL actual depend on a REST API?

- There is also like gRPC which is something to do with remote procedure calls.
    - what is a remote procedure call?


## Security
- Rate Limiting
- API key 
    - management of keys
    - generation of these keys (is it just symmetric encryption where the same key is used on the client and the server?)

## Design best practice
Recently I have begun working with OpenAPI when creating an API endpoint.
But what are some of the considerations which I should have when doing this.

From the swagger.io site:
- Nouns describe URLs better

Describe resource functionality with HTTP methods:
All resources have a set of methods that can be operated against them to work with the data being exposed by the API.
REstful apis comprise majorly of http methods which have well defined and unique actions against any resource.
Get - Use to retrieve a representation of a resource.
Post - Used to create new resources and sub-resources
Put/Patch - Used to update existing resources

### Responses - Give feedback to help developers succeed.
In general, there are three possible outcomes when using your API
1. The client application behaved erroneously - 400 response
2. The API misbehaved - 500
3. everything worked as expected 200.

### Requests
- Not actually sure what the correct use is for query parameters
- url components should probably be a noun
- post should be for creating a new thing
- although can also have it in the url for a get request for a partucular act

Question:
- What is best practice endpoint naming conventions?
- Should we be using POST requests with a payload or passing the relevant details in the HTTP request path?
- Using RSwag you can generate the openapi specification.
    N.B. we normally don't actually want to be hitting the api in the test but can just test the response codes.
    - This seems to just check the status code by default no other details.
    - Perhaps it checks that the response is in the same shape as the schema also?
    - This is indeed what happens as per the following source:
    https://github.com/rswag/rswag?tab=readme-ov-file#paths-operations-and-responses (Last line of this paragraph)
- This also unlocks being able to provide a client really easily using another gem (name of which I can't recall rn)
- How to deal with setting the default server when it will change when you are developing locally?

Notes:
An api defined using openapi specs can be divided into 3 main sections
- Meta information
The servers array specifies one or more server urls for api calls. The endpoint paths are appended to the server url.
- Path items (endpoints)
The path items are the endpoints of your API under which you can specify HTTP verbs for manipulating the resources.
Every response owuld need at least one HTTP status code to descrive the kind of responses a consumer is likely to expect.
### Parameters
Query Parameters
- The most common type of parameters. They appear at the end of a url following a question mark. They are optional and nonunique so that they can be specified multiple times in the URL. It is a non-hierarchical component of the URL.
These varialbes are defined under the parameters objec tin the openapi definition.

#### Request Body
Post, Put and patch requests typically contain the request body. The request body is defined by using the requestBody object.

#### Path parameters
The path parameters can be used to isolate a specific component of the data.


### Reusable components
In the example given in this article the schema is repeated outlining what is expected for different types of 200 responses.
e.g Artist name, genre etc.

Under the components section of the schema this can be added.
A reference to the schema can then dry up the spec where needed to reference the shape of the typical api response.

Sources:
https://support.smartbear.com/swaggerhub/docs/en/get-started/openapi-3-0-tutorial.html
https://swagger.io/resources/articles/best-practices-in-api-design/
ByteByteGo has a good diagram on the different http verbs and what they do which could be worth mentioning also.


RSwag
The run_test! thing does a bit of stuff under the hood which is probably good to be aware of.
Ok so when I was running this I really was not aware that there were keywords such as properties and items.
Which relate to object and arrays that are built from the official JSON Schema https://tour.json-schema.org/content/01-Getting-Started/02-Nesting-Objects.
I was just completely unaware of this really.
- Again worth noting that by default rswag does not have a strict validation in place,
required is only required if this is turned off in swagger_helper config.openapi_strict_schema
