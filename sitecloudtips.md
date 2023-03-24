## Cloud 

the site builder always crash for a page, download the page's metadata and upload back it.

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
