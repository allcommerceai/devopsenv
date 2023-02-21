# Unlocked Package


```
sfdx auth:web:login --setalias MyTP

sfdx auth web login -a MyTP

```

```
sfdx org list
```


```
git clone https://github.com/developerforce/GIFter.git
```


get gip key 

4YG0U44wt9yq72XwJMhMV80lpsPa4s27


--async
-f 

```
sfdx org create scratch -f config/project-scratch-def.json --async
```

#### Delete Org
sfdx org delete shape -o <value> [--json] [--api-version <value>] [-p]
```
sfdx org delete shape -o <username/alias>
```
  
  
  
#### About Package Dependencies
A key value of unlocked packages is that you can develop and maintain a set of interdependent packages.

An unlocked package can depend on an AppExchange package. If you are using an AppExchange package, you can put your own customization for that package in an unlocked package. When you install the unlocked package the AppExchange package must be present.
An unlocked package can depend on another unlocked package. Let’s say you’re creating a new app that employees can use to submit expense reports. It shares some backend integration functionality with your existing Payroll app. In this scenario, the expense report unlocked package will depend on the Payroll app unlocked package.
An unlocked package can depend on another unlocked package, and that unlocked package can, in turn, depend on a different unlocked package. Multiple levels of dependencies are supported.
You express dependencies in the packageDirectories section of the sfdx-project.json file. By supporting dependencies, unlocked packages promote modular development with a rich dependency framework. See the Salesforce DX Developer Guide for information on the project configuration file.
