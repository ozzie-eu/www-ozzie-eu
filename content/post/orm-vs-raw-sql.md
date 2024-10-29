---
title: "ORM vs. Raw SQL: A Performance Showdown"
date: 2024-10-29T12:38:26Z
draft: false
description: In the realm of data access, the choice between Object-Relational Mappers (ORMs) like Entity Framework (EF) Core and direct SQL approaches like Dapper can significantly impact application performance. This post delves into the nuances of each and explore a comparative analysis using .NET code examples.
tags:
- sqlserver
- dotnetcore
- C#
categories:
- backend
- Database
---

**ORM vs. Raw SQL: A Performance Showdown with Northwind Traders**

In the realm of data access, the choice between Object-Relational Mappers (ORMs) like Entity Framework (EF) Core and direct SQL approaches like Dapper can significantly impact application performance. Let's delve into the nuances of each and explore a comparative analysis using .NET code examples, benchmarking their performance against the classic Northwind Traders database.

**Understanding the Contenders**

* **ORM (Entity Framework Core):**
  - High-level abstraction: Maps object-oriented entities to database tables.
  - Reduced boilerplate code: Simplifies data access operations.
  - Automatic query generation: Generates SQL queries based on LINQ expressions.
  - Potential performance overhead: Due to the abstraction layer and query generation.

* **Raw SQL (Dapper):**
  - Low-level approach: Requires manual SQL query writing.
  - Enhanced performance: Direct execution of optimized SQL queries.
  - Greater flexibility: Fine-grained control over query execution.
  - Increased development effort: More manual coding and potential for SQL injection vulnerabilities.

**Performance Benchmarking with Northwind Traders**

To illustrate the performance differences, let's consider a benchmark scenario: retrieving a list of orders with their associated customer and order details.

**EF Core Example:**

```csharp
using Microsoft.EntityFrameworkCore;
using System.Data.SqlClient;
using System.Diagnostics;

// ...

static async Task BenchmarkEFCore(WideWorldImportersContext context)
{
    var stopwatch = new Stopwatch();
    stopwatch.Start();

    var orders = await context.Orders
        .Include(o => o.Customer)
        .Include(o => o.OrderLines)
        .ToListAsync();

    stopwatch.Stop();
    Console.WriteLine($"EF Core execution time: {stopwatch.ElapsedMilliseconds} ms");
}
```

**Dapper Example:**

```csharp
using Dapper;
using System.Diagnostics;

// ...

static async Task BenchmarkDapper(SqlConnection connection)
{
    var stopwatch = new Stopwatch();
    stopwatch.Start();

    var sql = @"
        SELECT o.*, c.*, ol.*
        FROM Sales.Orders o
        INNER JOIN Sales.Customers c ON o.CustomerID = c.CustomerID
        INNER JOIN Sales.OrderLines ol ON o.OrderID = ol.OrderID";

    var orders = (await connection.QueryAsync<Orders, Customers, OrderLines, Orders>(sql,
        (o, c, ol) =>
        {
            o.Customer = c;
            o.OrderLines.Add(ol);
            return o;
        }, splitOn: "CustomerID, OrderID"))
        .ToList();

    stopwatch.Stop();
    Console.WriteLine($"Dapper execution time: {stopwatch.ElapsedMilliseconds} ms");
}
```

**Key Performance Factors:**

The output of the full program will be similar to this one:
```
EF Core execution time: 3535 ms
Dapper execution time: 1322 ms
```
No matter how many time you execute the program, the order of difference between these two data retrievals will be the same. Dapper takes a little over 1/3 of the time spent by EF Core. However, if you change the program to repeat consecutively the same exact data retrieval, EF Core will start to have a better performance time than Dapper. This is because EF uses caching and change tracking.


1. **Query Complexity:**
   - **Simple Queries:** For straightforward queries, EF Core can often perform comparably to Dapper.
   - **Complex Queries:** Dapper excels in handling complex queries with joins, aggregations, and custom SQL functions, as it allows for precise optimization.

2. **Data Volume:**
   - **Small Datasets:** EF Core's overhead might be negligible.
   - **Large Datasets:** Dapper can significantly outperform EF Core, especially when dealing with massive data volumes.

3. **Application Architecture:**
   - **Micro-services:** Dapper's flexibility and lightweight nature can be advantageous in micro-service architectures.
   - **Monolithic Applications:** EF Core's abstraction layer can simplify development in monolithic applications.

**Balancing Performance and Productivity**

The optimal approach often lies in a hybrid strategy:

- **Leverage ORM for Rapid Development:** Use EF Core for simple CRUD operations and rapid prototyping.
- **Employ Raw SQL for Performance-Critical Scenarios:** Utilize Dapper for complex queries, large data sets, and performance-sensitive operations.

**Conclusion**

The choice between ORM and raw SQL is a trade-off between developer productivity and application performance. By carefully considering the specific requirements of your application, you can select the most appropriate approach to optimize both development time and execution speed. Remember to benchmark your specific use cases to make informed decisions.

If you'd like to try the benchmark yourself and reach to your own conclusions, the full C# program for this benchmark is available [here](https://gist.github.com/ozzie-eu/6af55841cd34c44d894b4e0b469e298f). 
