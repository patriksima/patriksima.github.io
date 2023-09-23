---
layout: post
title: Performance issues in business reporting
subtitle: How not to kill the database
tags: [linq,database,performance,reporting]
---

I love performance tasks. For obvious reasons, I immediately see the benefits of optimizations. Or the disappointment
when something goes wrong.

Reporting is usually complex and stressful for a database or other data source. It happens because.
A report is very often compiled from aggregated data. This means that in almost every case we have to pull data from many
database tables. And we use JOINs for this task.

Queries are often very complex and long and sometimes hard to understand.

This causes deadlocks, slows down the database and last but not least it impacts the work of the end users.

Of course, you can and probably should have a dedicated database for reporting. Let's clone a production database
synchronized somehow.

But... it costs something. And the client will push you to reduce maintenance and operational costs.

Another downside is the time it takes to create a report. So common practice is to run nightly jobs.
To create a report for a previous time period (day, week, month...).

It's not on demand.

So what is the solution.


## Idea

My idea is to build the report incrementally using events. This means that if the report data changes,
the system sends an event (hey, something has changed) and the reporting engine processes the event and modifies the current report.

## Demo

Let's dive into the example. It's the very trivial business activity app. Mainly it allows to store individual business cases,
especially the name of the salesman, the product he sold, the number of units, the total price, the date of sale.

Finally, we need a weekly overview of sales activity, especially which salesman have been most successful. For a reward.
The weekly report is a simple table with Year, Week, Best Agent, Most Sold Product, Quantity and Amount. 
So It's a weekly history of successful traders.

Components:
- Departments
- Agents
- Products
- Sales Log
- Weekly Report
- History

I've used Bogus (Faker) for random data like Departments, Agents and Products.

## How it works

You can try to add a business case. Open the Sales Log, select the agent, product, enter the quantity, adjust the total price and date
and finally hit the Add log button. That's it.

The app is using CQRS pattern. So the request is producing command _AddSalesLogCommand_. It ensures that your data
will be stored into the database.

And also, if the storing is successful, it is firing event _SalesLogAddedEvent_.

Handler for this event, does this in this order:
- check if there is a weekly report for the week when this business case occurred, if there is not, create a report and bail out.

``` csharp
if (reportWeek is null)
{
  await CreateReport(request, requestWeek, requestYear, requestAgent, requestProduct, cancellationToken);
  return;
}
```

- check if the total price of this case is better than the winner of the week, if so, update the report.

``` csharp
if (reportWeek.TotalPrice < request.Price)
{
   // update report with new max
   await UpdateReport(reportWeek, requestAgent.FirstName + " " + requestAgent.LastName,
   requestAgent.SalesAgentId, requestProduct.Name, request.Quantity, request.Price, cancellationToken);
   return;
}
```

- worst case scenario, recount the entire week and find a winner again.

``` csharp
  var winner = await GetBestSalesmanOfWeek(requestWeek, requestYear, cancellationToken);
  await UpdateReport(reportWeek, winner.Agent, winner.AgentId, winner.Product, winner.TotalProducts, winner.TotalPrice, cancellationToken);
```

## Conclusion ##

This example is only a proof-of-concept.

It has never been used in reality on complex reports. I have not verified that it works in real-word scenario,
it is maintainable, understandable for programmers and overall more convenient than the classic solution.

Still, if anyone is brave enough to try it, let me know how the result was and what advantages and disadvantages they encountered.

## Source Code ##

[Source code](https://github.com/patriksima/EventCachingDemo) is hosted by Github.
