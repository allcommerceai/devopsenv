# Data Import&Export realted SFDX

## data export

1. By write the Soql control just the related data is exported
```
sfdx force:data:tree:export --targetusername DevHubYourBrand --outputdir assets/data --query "SELECT Id, Name, Email__c, Phone__c, Mobile_Phone__c, Title__c, Picture__c, ( SELECT Id, Address__c, Assessed_Value__c, Baths__c, Beds__c, Broker__c, City__c, Date_Agreement__c, Date_Closed__c, Date_Contracted__c, Date_Listed__c, Date_Pre_Market__c, Description__c, Location__Longitude__s, Location__Latitude__s, Picture__c, Price__c, Name, State__c, Status__c, Tags__c, Thumbnail__c, Title__c, Zip__c FROM Properties__r ) FROM Broker__c"
```



## data import

```
sfdx force:data:tree:import --sobjecttreefiles data/Account.json


```
