---
type: example
summary: Redirect all requests from one domain to another domain.
goal:
  - Routing
operation:
  - Redirect
product:
  - Snippets
pcx_content_type: example
title: Redirect from one domain to another
layout: example
---

```js
export default {
  async fetch(request) {
    // Define variables to use in the response redirect.
    const base = "https://example.com";
    const statusCode = 301;

    // Clone the original URL.
    const url = new URL(request.url);

    // Define a "pathname" and "search" variables, extracting their values from the cloned URL.
    const { pathname, search } = url;

    // Define the destination URL using the variables you declared previously.
    const destinationURL = `${base}${pathname}${search}`;
    console.log(destinationURL);

    // Respond with the redirect.
    return Response.redirect(destinationURL, statusCode);
  },
};
```