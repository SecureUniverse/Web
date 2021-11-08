# CSRF

## Concepts
- Requests are not validated at the server side
- Server does not check if the user generatd the request
- Requests can be forged and sent to users to make them do things they don't intend to do such as changing their password

## Mitigation
- Generate an unpredictable token that can not be used (large value, random, unique)
- Embed the token in the HTML page in a hidden form
- Verify the token when the form is submitted 
