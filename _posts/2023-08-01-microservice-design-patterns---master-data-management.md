---
title: "Microservice Design Patterns - Master Data Management"
categories:
  - Posts
tags:
  - serverless
  - architecture
  - design-patterns
---

Master data management (MDM) is a design pattern for data distribution between micro services. Concept is pretty simple in theory. You create a micro service specifically to serve the whole data of your application. All data are stored under that micro service storages and served via one way or another. Other micro services either pull data from MDM service or MDM service pushes the data to those micro services in caches or temporary tables.

There are two options to access data from an MDM service:

1. Request/Response based: Any micro service access to MDM via its API when they need the data.
2. Pull based: All micro services periodically pull latest data from MDM. Much like using a stream, micro services asks the missing data starting from a given timeframe and get the difference. They generally store those data in their temp tables or disk caches.
3. Push based: When a change happens in MDM, it sends an event and all subscribed micro services stores those changes in their temp tables or disk caches.

First option puts a huge load to MDM service. How are you going to scale that service? Suppose that on average your micro services get 1000 request per second that may mean your MDM service may get 1000x # of micro services request / second. Is this even scalable?

Second option means your micro services never uses real time data. It depends on the period of your pull call but if every micro service pulls data every 5 minutes, you will always be 5 minutes late than actual data. Add network failures and possible outages to the services and at the end you will have unsynced micro services all around your application.

Third option seems reasonable unless you disregard network problems and downtimes. Those are real things that impacts even retrieval from micro services. At some point you will start losing data and this will create inconsistencies between micro services.

Second and third option also results to use a lot of caching and/or temporary tables to store the same amount of MDM data on the micro services. Then what is the purpose of the MDM anyway?

What does it bring:

- Unified data store and access
- Easy to implement frontend/backoffice applications. Just connect to a single service and manage all the data you need
- Prevents data duplication
- May help reduction of storage and database costs

What do we lose:

- Single point of failure. If that service fails, all services fail.
- Completely disregards single responsibility principle. You put all your eggs to the same bucket.
- Data synchronisation issues. No matter what you do (pull based or push based), services will be out of sync at some point which may cause serious issues.
- May degrade performance when used with request/response based approach

As you can see, I am not a big fun of MDM pattern in micro services. They are hard to maintain and most of the time, they are messed up and causes more trouble than their benefits. I think it is a poor man’s choice when you can’t implement a good discovery mechanism and a unified API between micro services. It is not a bad thing to give more responsibility to your micro services and handle only the required data in required micro services.
