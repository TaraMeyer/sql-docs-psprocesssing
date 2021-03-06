---
external help file: Microsoft.SqlServer.Management.PSSnapins.dll-Help.xml
online version: 
schema: 2.0.0
ms.assetid: 0E1098BE-B126-4A2E-82ED-7C07DBCA9B2A
updated_at: 12/8/2016 7:20 PM
ms.date: 12/8/2016
content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Suspend-SqlAvailabilityDatabase.md
original_content_git_url: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/master/sqlserver-cmdlets/sqlserver/vlatest/Suspend-SqlAvailabilityDatabase.md
gitcommit: https://github.com/MicrosoftDocs/sql-docs-powershell/blob/b925b18b49186ab91cfeb5201e061d569d0eeae2/sqlserver-cmdlets/sqlserver/vlatest/Suspend-SqlAvailabilityDatabase.md
ms.topic: reference
author: stevestein
ms.author: sstein
keywords: powershell, cmdlet
manager: jhubbard
open_to_public_contributors: true
ms.service: sql-server
---

# Suspend-SqlAvailabilityDatabase

## SYNOPSIS
Suspends data movement on an availability database.

## SYNTAX

### ByPath (Default)
```
Suspend-SqlAvailabilityDatabase [[-Path] <String[]>] [-Script] [-InformationAction <ActionPreference>]
 [-InformationVariable <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByObject
```
Suspend-SqlAvailabilityDatabase [-InputObject] <AvailabilityDatabase[]> [-Script]
 [-InformationAction <ActionPreference>] [-InformationVariable <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION
The **Suspend-SqlAvailabilityDatabase** cmdlet suspends data movement on an availability database.
This cmdlet suspends a database on the replica that is hosted by the current server instance.
If you suspend a secondary database, this cmdlet sets its state to SUSPENDED.
It falls behind the corresponding primary database.
If you suspend a primary database, data movement stops on every secondary replica.

## EXAMPLES

### Example 1: Suspend synchronization for a database
```
PS C:\>Suspend-SqlAvailabilityDatabase -Path "SQLSERVER:\Sql\Server\Instance\AvailabilityGroups\MainAG\AvailabilityDatabases\Database16"
```

This command suspends data synchronization for the availability database Database16 in the availability group named MainAG on the server instance named Server\Instance.

### Example 2: Suspend synchronization for all databases
```
PS C:\>Get-ChildItem "SQLSERVER:\Sql\Server\Instance\AvailabilityGroups\MainAG\AvailabilityDatabases" | Suspend-SqlAvailabilityDatabase
```

This command gets all the availability databases that belong to MainAG, and then passes them to the current cmdlet by using the pipeline operator.
The current cmdlet suspends each availability database.

### Example 3: Create a script to suspend a database
```
PS C:\>Suspend-SqlAvailabilityDatabase -Path "SQLSERVER:\Sql\Server\Instance\AvailabilityGroups\MainAG\AvailabilityDatabases\Database16" -Script
```

This command creates a Transact-SQL script that suspends the availability database named Database16 in the availability group named MainAG.
The command does not perform this action.

## PARAMETERS

### -Path
Specifies the path of an availability database that cmdlet suspends.
If you do not specify this parameter, this cmdlet uses current working location.

```yaml
Type: String[]
Parameter Sets: ByPath
Aliases: 

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script
Indicates that this cmdlet returns a Transact-SQL script that performs the task that this cmdlet performs.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InformationAction
Specifies how this cmdlet responds to an information event.

The acceptable values for this parameter are:

- Continue
- Ignore
- Inquire
- SilentlyContinue
- Stop
- Suspend

```yaml
Type: ActionPreference
Parameter Sets: (All)
Aliases: infa

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InformationVariable
Specifies an information variable.

```yaml
Type: String
Parameter Sets: (All)
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject
Specifies availability database, as an **AvailabilityDatabase** object, that this cmdlet suspends.

```yaml
Type: AvailabilityDatabase[]
Parameter Sets: ByObject
Aliases: 

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### Microsoft.SqlServer.Management.Smo.AvailabilityDatabase
You can pass an availability database to this cmdlet.

## OUTPUTS

## NOTES
* The instance on which you run this command must be enabled for high availability.

## RELATED LINKS

[Add-SqlAvailabilityDatabase](xref:sqlserver/vlatest/Add-SqlAvailabilityDatabase.md)

[Remove-SqlAvailabilityDatabase](xref:sqlserver/vlatest/Remove-SqlAvailabilityDatabase.md)

[Resume-SqlAvailabilityDatabase](xref:sqlserver/vlatest/Resume-SqlAvailabilityDatabase.md)


