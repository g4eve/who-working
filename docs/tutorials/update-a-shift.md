---
layout: page
---

# Tutorial: Find a specific shift and update two properties

In this tutorial, you learn how to find a closed shift and update twp propetties with the `PATCH` METHOD. Knowing how to update a shift helps store managers save time. They can quickly generate new a shift from a previous record and avoid creating a new shift from scratch.

Expect this tutorial to take about 15 minutes to complete.

## Before you start

Make sure you've completed the [Before you start a tutorial](before-you-start-a-tutorial) topic on the development system you'll use for the tutorial.

## Find an existing shift

The first step is to display a list of shifts with a CLOSED status, find the record that needs to be updated, and then make a note of the ID number. Viewing specific a shift record requires a (`GET`) method.

1. Open the Postman app on your desktop.
1. In the Postman app, create a new request with these values:
    * **METHOD**: GET
    * **URL**: `{base_url}/shifts?status=closed`
    * **Headers**:`Content-Type: application/json`
    * **Request body**: None

1. In the Postman app, choose **Send** to make the request. The service returns a JSON object that contains all closed shifts. Each shift has the following format. Note the `id` of the shift to update.

        ```js
     {
        "id": "03b6",
        "date": "2024-06-11",
        "start_time": "0900",
        "shift_length": "6",
        "warning": "opening",
        "location_detail": "Eatons Centre",
        "status": "closed"
    },
    {
        "id": "03d3",
        "date": "2024-06-11",
        "start_time": "0900",
        "shift_length": "6",
        "warning": "opening",
        "location_detail": "Eatons Centre",
        "status": "closed"
    }
        ```

## Update shift information

Now that you know the shift id, send a PATCH request to the /shifts/{id} endpoint to update the description.

To update the task description:

In Postman, add a new request with these values:
    * **METHOD**: PATCH
    * **URL**: `{base_url}/shifts/{id}`
    * **Headers**:`Content-Type: application/json`
    * **Request body**: None

In the Request Body, add only the updated property and parameter. In this example, the status changes from `OPEN` to `CLOSED`.

{
        "status": "closed"
}

1. Click Send. The service updates the shift status and returns a 200 OK along with the updated task as a JSON object.

```js

{
    "id": "03b6",
    "date": "2024-06-11",
    "start_time": "0900",
    "shift_length": "6",
    "warning": "opening",
    "location_detail": "Eatons Centre",
    "status": "open"
}
 ```

## Next Steps

Now that you have verified this API workflow in Postman, you’re ready to integrate it into your application. For more information, contact your customer success manager.

## Related Topics

Task resource
Handing errors
