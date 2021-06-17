---
title: Trigger Values
position: 1
---
<details>
  <summary> aham</summary>

| Amount | Status        | Error Message                      |
|------|-------------|----------------------------------|
| 0.00  | SUCCESS          |           -                |
| 0.01  | SUCCESS     |            -    |
| 0.02  | SUCCESS |   -    |
| 0.03  | SUCCESS   | -     |
| 0.04  | ERROR   | Refer to card issuer     |
| 0.05  | ERROR   | Refer to card issuer, special condition     |
| 0.06  | ERROR   | Invalid merchant     |

 </details>
All errors will return JSON in the following format:

~~~ json
{
  "error": true,
  "message": "error message here"
}
~~~
