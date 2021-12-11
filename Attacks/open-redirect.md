# Open Redirect

## Concept
- https://example.com/login/?nextPage=https://google.com => Allowed
- https://example.com/login/?nextPage=https://evilsite.com => Not allowed

## Payload
- https://example.com/login/?nextPage=https://evilsite.com/?google.com
- https://example.com/login/?redirect=https://www.evilsite.google.com
- https://example.com/login/?nextPage=https:///www.google.com@evilsite.com
