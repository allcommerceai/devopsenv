
### Lightning Out to make Flow used outside Salesforce

```
<!-- myFlowWrapper.html -->
<template>
    <lightning-card title="My Flow">
        <div class="slds-m-around_medium">
            <lightning-flow flow-name="Your_Flow_API_Name"></lightning-flow>
        </div>
    </lightning-card>
</template>


```

```

<!-- flowWrapperApp.app -->
<aura:application extends="ltng:outApp" access="GLOBAL">
    <aura:dependency resource="c:myFlowWrapper"/>
</aura:application>


```

Inexternal site setting

```
<script src="https://<your_instance>.lightning.force.com/lightning/lightning.out.js"></script>

```


```
<div id="flowContainer"></div>

```



```
lightning.use("c:flowWrapperApp", function() {
    lightning.createComponent(
        "c:myFlowWrapper",
        {},
        "flowContainer",
        function (component) {
            console.log("Flow wrapper component created");
        }
    );
});

```


##### Setup > CORS and adding a new entry with the external site's domain.


```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>External Site with Flow</title>
    <script src="https://<your_instance>.lightning.force.com/lightning/lightning.out.js"></script>
</head>
<body>
    <div id="flowContainer"></div>

    <script>
        // Replace YOUR_ACCESS_TOKEN with the actual access token and YOUR_INSTANCE with your Salesforce instance name
        const accessToken = 'YOUR_ACCESS_TOKEN';
        const instance = 'https://YOUR_INSTANCE.lightning.force.com';

        const lightning = $Lightning.use('c:flowWrapperApp', function () {
            $Lightning.createComponent(
                'c:myFlowWrapper',
                {},
                'flowContainer',
                function (component) {
                    console.log('Flow wrapper component created');
                }
            );
        }, instance, accessToken);
    </script>
</body>
</html>


```
