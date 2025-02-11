---
title: "sysmail_help_profile_sp (Transact-SQL)"
description: "sysmail_help_profile_sp (Transact-SQL)"
author: markingmyname
ms.author: maghan
ms.date: "03/14/2017"
ms.service: sql
ms.subservice: system-objects
ms.topic: "reference"
f1_keywords:
  - "sysmail_help_profile_sp_TSQL"
  - "sysmail_help_profile_sp"
helpviewer_keywords:
  - "sysmail_help_profile_sp"
dev_langs:
  - "TSQL"
---
# sysmail_help_profile_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Lists information about one or more mail profiles.  
  
 :::image type="icon" source="../../includes/media/topic-link-icon.svg" border="false"::: [Transact-SQL syntax conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```  
  
sysmail_help_profile_sp  [   [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' ]  
```  
  
## Arguments  
`[ @profile_id = ] profile_id`
 The profile id to return information for. *profile_id* is **int**, with a default of NULL.  
  
`[ @profile_name = ] 'profile_name'`
 The profile name to return information for. *profile_name* is **sysname**, with a default of NULL.  
  
## Return Code Values  
 0 (success) or 1 (failure)  
  
## Result Sets  
 Returns a result set with the following columns.  
  
| Column name | Data type | Description |
| ----------- | --------- | ----------- |
|**profile_id**|**int**|The profile id for the profile.|  
|**name**|**sysname**|The profile name for the profile.|  
|**description**|**nvarchar(256)**|The description for the profile.|  
  
## Remarks  
 When a profile name or profile id is specified, **sysmail_help_profile_sp** returns information about that profile. Otherwise, **sysmail_help_profile_sp** returns information about every profile in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
 The stored procedure **sysmail_help_profile_sp** is in the **msdb** database and is owned by the **dbo** schema. The procedure must be executed with a three-part name if the current database is not **msdb**.  
  
## Permissions  
 Execute permissions for this procedure default to members of the **sysadmin** fixed server role.  
  
## Examples  
 **A. Listing all profiles**  
  
 The following example shows listing all profiles in the instance.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp;  
```  
  
 Here is a sample result set, reformatted for line length:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
57          AdventureWorks Operator       Operator mail profile.          
```  
  
 **B. Listing a specific profile**  
  
 The following example shows listing information for the profile `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
 Here is a sample result set, reformatted for line length:  
  
```  
profile_id  name                          description  
----------- ----------------------------- ------------------------------  
56          AdventureWorks Administrator  Administrative mail profile.    
```  
  
## See Also  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
