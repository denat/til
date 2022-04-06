# Mock GraphQL APIs using msw

The most common usages of msw I've seen throughout the web, and from my own experience, involved mocking REST APIs. Turns out, msw is just as good for mocking GraphQL APIs!

```typescript
import { graphql } from "msw";

interface Variables {
  firstName: string;
  lastName: string;
}

interface Response {
  id: string;
  email: string;
  firstName: string;
  lastName: string;
}

graphql.mutation<Response, Variables>("UpdateUserDetails", (req, res, ctx) => {
  const { firstName, lastName } = req.variables;
  return res(
    ctx.data({
      user: {
        id: "c322bda3-5d5f-45c2-90eb-f94571dd951d",
        email: "daisy.doe@example.com",
        firstName: "Daisy",
        lastName: "Doe",
      },
    })
  );
});
```