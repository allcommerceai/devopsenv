# Given the permission set name and remove the allocations




```
 Database.delete([
		SELECT Id
		FROM PermissionSetAssignment
		WHERE PermissionSet.Name = 'ChatGPT_Access'
]);

```
