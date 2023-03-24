
###

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
