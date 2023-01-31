---
title: "This is why you're not better off with a commercial database"
description: When tackling a new enterprise project to support a given business, you face the challenge of choosing and committing to a database platform. The choice should be the one most adequate, given the needs and requirements of the new information system and data to be hosted and managed.
date: 2023-01-31T08:30:20Z
draft: false
categories:
- Backend 
---
![Database](database-marker.webp)
When tackling a new enterprise project to support a given business, you face the challenge of choosing and committing to a database platform. The choice should be the one most adequate, given the needs and requirements of the new information system and data to be hosted and managed.

Typically, several factors should be taken into consideration like security features, storage requirements, reliability, high availability, backups, disaster recovery, data compression, technical support, and last but not least, the cost of the solution. Added to that there are also performance, scalability, and ease of administration to think about.
With the result of this analysis, most of the time, the verdict is this: data platforms available as community editions or free open source fall short of the given requirements fulfillment. So, the advice is almost always to acquire commercial licenses or expand the licensing already owned.
And this should give you peace of mind for a while. At least until the first release of the system goes live. After that, some of the common pitfalls are:

* Security permissions were not exhaustively identified for all database objects. To solve things quickly, you turn your database authorization management into Swiss cheese;

* The new system has issues, until the bugs are fixed, manual correction scripts have to be executed during working hours, maiming overall business activity;

* As the data volume grows, there is performance degradation due to inefficient indexing, bad user experience design, or poor database coding skills;

* Technical support provided by the database vendor performs an audit on the workload, does some tuning on the server instance, and shifts responsibility for the remaining lack of performance over to the development team;

* The development team struggles to adopt the database vendor recommendations as it has a great impact on the source code;

* Management wants high availability, but it won’t commit the infrastructure resources and budget to set it up properly;

* You do not have a remote site so that a disaster recovery plan can be made, you don’t have a lab where you regularly restore backups and perform automated integrity checks;
You are understaffed and with no one possessing deep skills on the specific data platform you own;

Even if just a third of these pitfalls sound familiar, what are you doing with your next project? Are you still thinking of recommending commercial software because people are the ones to blame here?

On a global organization, after you deploy the first release and spread it across the offices, the licensing and support costs will skyrocket. That money could be spent preventing some of the pitfalls mentioned here. If you cut back on licensing and support, you can spend on infrastructure and staff.
There are wonderful commercial databases out there, but in the business requirements phase, the pick should be done as a whole and not based on vendor promises because the final solution will be a result of development and available budget, not a sales brochure.

Vision and engineering are the keys to success. And I’m afraid that doesn’t come out of the box.
