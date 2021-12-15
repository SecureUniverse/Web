# Open Redirect

## Concept
- Allowed: https://example.com/login/?nextPage=https://google.com
- Not allowed: https://example.com/login/?nextPage=https://evilsite.com

## Payload
- https://example.com/login/?nextPage=https://evilsite.com/?google.com
- https://example.com/login/?redirect=https://www.evilsite.google.com
- https://example.com/login/?nextPage=https:///www.google.com@evilsite.com
