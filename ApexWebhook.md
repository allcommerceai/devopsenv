# Webhook in Apex/Salesforce


In Salesforce, webhooks can be implemented using Apex, a custom language provided by Salesforce. You can create an Apex class to send an HTTP request to the webhook endpoint. Here's a sample Apex class to create a webhook for a third-party service:

```

public class WebhookHandler {
    // Set the webhook URL
    public static final String WEBHOOK_URL = 'https://example.com/webhook/endpoint';

    // Main function to send a webhook
    public static void sendWebhook(String message) {
        // Prepare the HTTP request
        HttpRequest req = new HttpRequest();
        req.setEndpoint(WEBHOOK_URL);
        req.setMethod('POST');
        req.setHeader('Content-Type', 'application/json;charset=UTF-8');

        // Prepare the payload
        Map<String, Object> payload = new Map<String, Object>();
        payload.put('message', message);

        // Convert the payload to JSON
        String jsonPayload = JSON.serialize(payload);

        // Set the request body
        req.setBody(jsonPayload);

        // Send the request
        Http http = new Http();
        HttpResponse res;
        try {
            res = http.send(req);
            System.debug('Response Status: ' + res.getStatus());
            System.debug('Response Status Code: ' + res.getStatusCode());
        } catch (Exception e) {
            System.debug('Error: ' + e.getMessage());
        }
    }
}


```

To use this webhook, you can call the sendWebhook function from a trigger or another Apex class. For example, you can create a trigger that sends a webhook when a new Account is created:




```

trigger AccountWebhook on Account (after insert) {
    for (Account newAccount : Trigger.new) {
        String message = 'New account created: ' + newAccount.Name;
        WebhookHandler.sendWebhook(message);
    }
}


```



This example demonstrates how to create a simple webhook in Salesforce using Apex. You can modify the code to meet your specific requirements, such as adding custom fields or data to the payload, changing the webhook URL, or adjusting the HTTP request method.
