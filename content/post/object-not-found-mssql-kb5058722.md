---
title: "The 'object not found' Error After Applying KB5058722 on SQL Server 2019 CU32"
date: 2025-08-04T23:30:44+01:00
draft: false
description: With the release of security update KB5058722 (SQL Server 2019 CU32) on July 8, 2025, some administrators and developers reported encountering the error "object not found" when accessing objects outside the default `dbo` schema. This post explains the root cause of this issue, why it occurs after the update, and how to address it.
tags:
- sqlserver
categories:
- database
- Backend 

---
With the release of security update KB5058722 (SQL Server 2019 CU32) on July 8, 2025, some administrators and developers reported encountering the error "object not found" when accessing objects outside the default `dbo` schema. This post explains the root cause of this issue, why it occurs after the update, and how to address it.

### What Changed with KB5058722?

Update KB5058722 addresses multiple security vulnerabilities identified in SQL Server, including information disclosure risks and remote code execution threats. As part of enhanced security, SQL Server now enforces stricter rules regarding object name resolution and the explicit use of schemas.

### Why Does This Error Occur Outside the dbo Schema?

Historically, when a T-SQL statement referenced an object without specifying its schema, SQL Server would first look in the user’s default schema and then in `dbo`. In many setups, objects outside `dbo` were accessed without the schema name, relying on this search order. After KB5058722, this logic is more restrictive:

- Referencing stored procedures, tables, or functions without specifying a schema may now result in an "object not found" error for non-`dbo` objects, as SQL Server might no longer resolve the correct schema automatically for that user.
- Especially if permissions, roles, or default schemas have changed (a common occurrence following security reviews or updates), context may now default solely to `dbo`, ignoring custom schemas used by applications or legacy users.


### Example of the Issue

**Common mistake when accessing an object outside dbo:**

```sql
-- Assuming a table exists in another schema, e.g. "finance.despesas"
SELECT * FROM despesas; -- May result in "object not found"
```

**Reason**: SQL Server looks for `dbo.despesas` and does not find `finance.despesas`.

### Best Practices After the Update

To mitigate this problem and ensure scripts remain compatible:

- **Always specify the schema when referencing objects:**

```sql
SELECT * FROM finance.despesas;
```

- Review objects, procedures, and jobs that might assume `dbo` as the default schema.
- Update permissions and user mappings to ensure the correct default schema, if strictly necessary.
- Test automated routines and orchestrations that might be affected by the changed behavior after the update.


### General Recommendations

- **Do not rely on the default schema:** Use explicit schema references in all scripts and applications.
- **Check users and roles:** If roles or permissions (such as `sysadmin`) were changed after applying the update, revalidate user schema containers.
- **Document schema standards:** Ensure your team follows best practices for future development and maintenance.


### Conclusion

The "object not found" error after KB5058722 is not a bug, but rather an intentional result of strengthened security and object resolution policies in SQL Server. Issues like this highlight the need for good schema usage practices. This is a protective measure, not a limitation of the update. Always use explicit schema references to prevent future issues and keep your environments secure and up to date.

### References

- [KB5058722 - Description of the security update for SQL Server 2019 CU32: July 8, 2025](https://support.microsoft.com/en-us/topic/kb5058722-description-of-the-security-update-for-sql-server-2019-cu32-july-8-2025-09dc5da9-3a60-4462-a8ac-a8e782d088d5)
- [Fixes an issue that was introduced in a previous Windows](https://devicebase.net/en/microsoft-sql-server-2019/updates/kb5058722-fixes-an-issue-that-was-introduced-in-a-previous-windows/74y)
- [Microsoft SQL Server 0-Day Vulnerability Exposes Sensitive Data . . .](https://cybersecuritynews.com/microsoft-sql-server-0-day-vulnerability/)

