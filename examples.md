
# Examples

<br>

## Compose and Import Tests

_Is there a demo API I can use to build and test with?_  
> _Yes! Try using the HTTP Client._
> 
> - Open a project > Select _`Create Test`_ > Select _`HTTP Client`_  
>   - Keep the default _`GET`_ request type.  
>   - Enter the _`Request URL`_ as _`http://demoapi.apifortress.com/api/retail/product`_  
>   - Select the _`Headers`_ tab.
>       - Add a key name _`key`_
>       - Assign it the value _`ABC123`_  
> - Select the blue _`SEND`_ button and examine the response body.
> - Select the green _`Generate Test`_ button.  
> 

<br>

_Do you know if there are any examples I could import?_
> _Yes!_ 
> - Open a project > Select _`Create Test`_ > Select _`APIF Test` (Import from an exported API Test)_  
>   - Select the [test-examples.zip][api-test-example] file.



<br>

_How do I use multiple API calls in a single test?_  

> 
> _By "chaining" I/O and Logic components, a response can be used as part of a subsequent request._  
> - Common use cases include.
>   - Select a random sample of items from one response and validate each against another endpoint. 
>   - Request a token from one endpoint and use it in a request against another endpoint.
>
> 
> Import the workshop examples and review the tests listed below.
> - _`product integration`_
> - _`authorisation flow`_


<br>
<br>


## Deploy API Mocking Server

Please supplement the quick start examples provided here by referencing the [source documentation][api-docs-mocking] which details the benefits, use cases, and provides specific usage.


### Requirements

- Docker
- Examples use `curl` and `jq`.

### Set your enviornment variables.

[Create a Webhook][api-create-webhook] for the target project. This allows us to log the examples we process.


```
SAUCE_USERNAME=
SAUCE_ACCESS_KEY=
SAUCE_API_PROJECT_HOOK_ID=
```

### Mocking Mode

Use an OpenAPI spec file to serve static and dynamic responses, while validating that both the example requests and responses are compliant with the contract, and log the transactions to the Sauce API Testing project logger.

```sh
# start the mocking server
./etc/start-030-piestry-logger


# example 1 / validated request with dynamically generated response
curl --config ./etc/curl.conf http://localhost:6000/api/retail/product |jq


# example 2 / bad request / consumer contract violation
productId="one"
curl --config ./etc/curl.conf http://localhost:6000/api/retail/product/${productId} |jq


# example 3 / validated request with static response from ./specs/examples/user_id_3.json / response passes schema validation
userId="3"
curl --config ./etc/curl.conf http://localhost:6000/api/user/${userId} |jq


# example 4 / validated request with static response from ./specs/examples/user_id_4.json / response fails schema validation
userId="4"
curl --config ./etc/curl.conf http://localhost:6000/api/user/${userId} |jq
```

#### E2E Mode

Contract validation against the actual origin! Instead of capturing messages to the project logger, we'll place these in the project dashboard and set a build id to group them and save the response locally.


```sh
# start the mocking server
./etc/start-035-piestry-e2e


# example 1 / request and response both pass validation / response is from the live API
curl --config ./etc/curl.conf http://localhost:6000/api/retail/product |jq


# example 2 / bad request / consumer contract violation
productId="one"
curl --config ./etc/curl.conf http://localhost:6000/api/retail/product/${productId} |jq


# example 3 / request and response both pass validation / response is from the live API
productId="2"  
curl --config ./etc/curl.conf http://localhost:6000/api/retail/product/${productId} |jq


# example 4 / valid request and with 404 response from live API / item not found
productId="200"
curl --config ./etc/curl.conf http://localhost:6000/api/retail/product/${productId}


# example 5 / valid request and with 404 response from live API / route not found
userId="1"
curl --config ./etc/curl.conf http://localhost:6000/api/user/${userId}
```




[api-test-example]: ./specs/test-examples.zip
[api-docs-mocking]: https://docs.saucelabs.com/api-testing/mocking/
[api-create-webhook]: https://docs.saucelabs.com/api-testing/logger/#running-the-logger




