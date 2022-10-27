
## Sauce Labs API Testing Resources

<br>

 A centralised and collaborative environment with tools to quickly generate functional and end-to-end API tests, deploy a mocking server that mimics a real API server's calls and responses, and load test your endpoints.

- [Contract Testing][api-contract]  
- [Mocking][api-mock]  
- [Load Testing][api-load]  

<br>

The API [_Testing Composer_][api-composer] provides an environment to automatically generate tests, code them from scratch, or import them from a spec file. Enhance your tests with four powerful _component_ types and JavaScript support.

- [I/O][api-composer-io] — GET, POST, PUT, PATCH, DELETE
- [Assert][api-composer-assert] — Compare, Contains, Exists, Is
- [Logic][api-composer-logic] — Loops, Conditionals
- [Fn][api-composer-fn] — Flow, Fact, Fake, and more!

<br>


Once you've written a few tests, use [_API methods_][api-methods] and the [_apictl_][api-ctl] tool to automate your workflows and integrate them into a pipeline.



<br>

### Examples

<br>

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
> - Select the gree _`Generate Test`_ button.  
> 

<br>

_Are there examples I could import?_
> _Yes!_ 
> - Open a project > Select _`Create Test`_ > Select _`APIF Test` (Import from an exported API Test)_  
>   - Select the [workshop-examples.zip][api-example-01] file.



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





[api-composer]: https://docs.saucelabs.com/api-testing/composer
[api-composer-io]: https://docs.saucelabs.com/api-testing/composer/io-components
[api-composer-assert]: https://docs.saucelabs.com/api-testing/composer/assertion-components
[api-composer-logic]: https://docs.saucelabs.com/api-testing/composer/logical-components
[api-composer-fn]: https://docs.saucelabs.com/api-testing/composer/other-components

[api-mock]: https://docs.saucelabs.com/api-testing/mocking
[api-load]: https://docs.saucelabs.com/api-testing/load-testing
[api-contract]: https://docs.saucelabs.com/api-testing/contract-testing

[api-methods]: https://docs.saucelabs.com/dev/api/api-testing
[api-ctl]: https://docs.saucelabs.com/api-testing/integrations/apifctl-cicd-integration/#apifctl-commands

[api-example-01]: ./workshop-examples.zip