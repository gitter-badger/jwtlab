# JWTLAB

This is a simple example of JWT usage for authentication with python on server side and angularjs on client side.

## What is JWT?

JWT (JSON Web Token) is compact and self-contained way for securely transmitting information between parties as a JSON object defined on a RFC (#7519). 

The main usage for JWT may be for authentication/authorization purposes but it can be used also for exchanging information between parties.

## What does JWTLAB do?

It runs a webserver (Flask) on at localhost, port 5000, exposing the following routes:

1. `/signin`: receives a login/password combinades and validates it. If it's correct, the response will contain a authentication token.
2. `/public`: a simple endpoint that doesn't demands a valid token.
3. `/restricted`: a simple endpoint that demands a valid token.

## How to run JWTLAB?

1. install requirements
`
pip install -r requirements.txt
`
2. run the Flask app
`
python server.py
`
3. access `http://localhost:5000` with your browser.
4. to login use any of the credentials in `users.json`.

## How to test it?

You can test it surfing with your browser or using curl in your bash:

1. authenticate and store token

   ``
   token=`curl -H "Content-Type: application/json" -X POST -d '{"email":"scott@gmail.com", "password":"12345"}' http://localhost:5000/signin`
   ``

2. access a restricted area

   `
   curl -X GET http://localhost:5000/restricted -H "Authorization: Bearer $token"
   `


