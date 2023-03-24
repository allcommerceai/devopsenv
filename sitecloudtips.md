## Experence Cloud 

the site builder always crash for a page, download the page's metadata and upload back it.
Need open the setting under experience cloud to support "**ExperienceBundle Metadata API**"

Create a file package.xml
```

<?xml version="1.0" encoding="UTF-8"?>
<Package xmlns="http://soap.sforce.com/2006/04/metadata">
    <types>
        <members>*</members>
        <name>ExperienceBundle</name>
    </types>
    <version>53.0</version>
</Package>


```


```
sfdx force:mdapi:retrieve -s -r ./mdapipkg  -k package.xml
```

Compare and certain what is changed, update directly in metadata file, and upload back


### Expeirence Cloud - make LWC support 
Web2Lead - Lwc component with **webtolead** html code support

### Google Places API for Appointments - Territory Resources


### Use Aura App to support lwc testing 

create a Aura App with name **lwcApp**

```
<aura:application extends="force:slds">
    <c:partnerApplication/>
</aura:application>

```


```
https://yourdomain.lightning.force.com/c/lwcApp.app
```


### Flow Can be used in Experience Cloud

### LWC can be used in a flow screen to enhance the function


### Used in site, lunch flow in Modal
https://github.com/salesforce-experiencecloud/LaunchFlowInModal

### Make Tabs

### Make Record List





