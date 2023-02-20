# Data Import&Export realted SFDX

```
USAGE
  $ sfdx data COMMAND

TOPICS
  data create  create a record
  data delete  delete a single record or multiple records in bulk
  data export  export data from your org
  data get     get a single record
  data import  import data via the tree api
  data query   query records
  data update  update a single record
  data upsert  upsert many records via the bulk API
```

## data export

1. By write the Soql control just the related data is exported
```
sfdx force:data:tree:export --targetusername DevHubYourBrand --outputdir assets/data --query "SELECT Id, Name, Email__c, Phone__c, Mobile_Phone__c, Title__c, Picture__c, ( SELECT Id, Address__c, Assessed_Value__c, Baths__c, Beds__c, Broker__c, City__c, Date_Agreement__c, Date_Closed__c, Date_Contracted__c, Date_Listed__c, Date_Pre_Market__c, Description__c, Location__Longitude__s, Location__Latitude__s, Picture__c, Price__c, Name, State__c, Status__c, Tags__c, Thumbnail__c, Title__c, Zip__c FROM Properties__r ) FROM Broker__c"


sfdx data export -q "Select Id, name, (SELECT Id, LastName, FirstName FROM Contacts) from Account limit 10" --outputdir assets/data

```


a file Account-Contact.json created


## data import

```
sfdx data import tree --files assets/data/Account-Contact.json

```

```
USAGE
  $ sfdx data import tree -o <value> [--json] [--api-version <value>] [-f <value> | -p <value>]
    [--config-help]

FLAGS
  -f, --files=<value>...    Comma-separated and in-order JSON files that contain the records, in
                            sObject tree format, that you want to insert.
  -o, --target-org=<value>  (required) [default: test-urktm0h4gafy@example.com] Username or alias of
                            the target org.
  -p, --plan=<value>        Plan definition file to insert multiple data files.
  --api-version=<value>     Override the api version used for api requests made by this command
  --config-help             Display schema information for the --plan configuration file to stdout; if
                            you specify this flag, all other flags except --json are ignored.

```

## 
