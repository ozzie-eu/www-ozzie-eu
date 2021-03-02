---
title: "Umbraco Forms Translations"
description: "Umbraco consent warning translations not working."
date: 2021-03-02T15:47:06Z
draft: false
---
Last year I evaluated the [Umbraco Forms](https://umbraco.com/products/umbraco-forms/) product to migrate some existing forms and build new ones.
Despite being overall satisfied, I  stumbled upon [an issue](https://github.com/umbraco/Umbraco.Forms.Issues/issues/376) with form control translation. The consent warning translations were not working.
Being Umbraco a developer-friendly CMS, the [workaround solution](https://our.umbraco.com/documentation/Add-ons/umbracoforms/developer/extending/adding-a-fieldtype) was easy enough to come by and extend with this piece of code:

{{< gist ozzie-eu e379389e73fd352996ea524c6762a716 >}}

Anyway, the good news is the issue is closed as of today with a report that it's working fine on the upcoming 8.7.0 release.
