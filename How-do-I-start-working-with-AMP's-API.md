### Prerequisites

In order to use the API you must first have at least basic knowledge of how to send http POST requests in the language of your choice, you will also need to have a valid login to the instance in which you wish to perform API actions on.

### Introduction

Using the AMP API is very simple and can be integrated with almost every language. API calls are made by sending a http POST request containing JSON content to an endpoint URL that varies depending on what API action you want to perform. 

AMP helpfully provides a list of all possible API calls which can be found at `{YOUR PANEL URL HERE}/API`

### Call Format

As mentioned above, all calls to the API are given in JSON format with the two main components of a call being the: SESSIONID, and arguments. The SESSIONID can be found by calling the login method, which is discussed below. The arguments are optionally depending on what API method you wish to call, conveniently this is also listed in the API browser. 

### Starting

Before performing actions using the API made you must first authenticate with it by calling the Login method. ln the API browser you can find the login method which displays all necessary information about how to make the call. 

The following is an example of a valid call to the API to perform the login action: `{"username":"Bob","password":"IAmAFatChicken","token":"","rememberMe":"false"}` When creating calls there are two exceptions to the above-mentioned 'template'. In the above example you may notice there is no SESSIONID parameter, this is because the login method generates the session id **which must be passed with every other API call in order for it to perform it's job**. 

Now we have the data that has to be sent we need to know where to send it. For each API call the API browser will give you all the information you need to call that method. For example, to call the Login method you would send the request to `{YOUR PANEL URL}/API/Core/Login`. 


