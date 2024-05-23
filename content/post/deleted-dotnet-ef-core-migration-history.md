---
title: "Recover deleted .net EF Core Migration History Table"
date: 2024-05-23T16:02:02+01:00
draft: false
description: Working with Microsoft EF Core you might need to recover the records on the entity framework migration history table. Here's an easy way to do it.
tags:
- sqlserver
- dotnetcore
- C#
categories:
- backend
- Database
---
Working with Microsoft EF Core you might need to recover the records on the entity framework migration history table. Here's an easy way to do it, right from Visual Studio's Package Manager Console.

If you're using migrations, for sure you have used [Microsoft.EntityFrameworkCore.Tools](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Tools). this tools make available a set of Cmdlets, the one we need for the task in hand is Get-Migration.

First of all, go to the Nuget Package Manager and check which version of the EF package you are using. For the sake of example, I'll use version '7.0.5'.
Next, open your favorite text editor and copy the following script:
```
# Get migration IDs
$migrationIds = Get-Migration -noConnect | Select-Object -ExpandProperty Id

# Loop through each migration ID
foreach ($id in $migrationIds) {
  # Generate INSERT statement with placeholder for applied date
  $insertStatement = "INSERT INTO [__EFMigrationsHistory] (MigrationId, ProductVersion) VALUES ('$id', '7.0.5')"
  
  # Write INSERT statement with formatted current date
  Write-Output ($insertStatement)
}
```

Remember to replace '7.0.5' with your version. Save the script as a **.ps1** file into your project folder. Go to Visual Studio and call the script from the Package Manager Console.The console should output the needed insert statements to restore the migration history records.

Of course, if you really mucked up and dropped the actual table from the database, you have to create it, before running the SQL insert statements. For this you can use this **CREATE** statement on the database:
```
CREATE TABLE [dbo].[__EFMigrationsHistory](
	[MigrationId] [nvarchar](150) NOT NULL,
	[ProductVersion] [nvarchar](32) NOT NULL,
 CONSTRAINT [PK___EFMigrationsHistory] PRIMARY KEY CLUSTERED 
(
	[MigrationId] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
```

To get the insert statements output to a text file just redirect the output to a file, for instance, if you called your script 'Repopulate-Migrations.ps1', run:
```
Repopulate-Migrations.ps1 > out.txt
```

Hope this helps.