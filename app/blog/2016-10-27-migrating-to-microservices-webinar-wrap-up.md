---
layout: post
title: 'Migrating to Microservices: Webinar Wrap-Up'
date: '2016-10-27T06:05:06+03:00'
tags: []
tumblr_url: https://blog.mist.io/post/152363654471/migrating-to-microservices-webinar-wrap-up
---
Thanks so much to all who turned out for last week’s Moving from Monolith to Microservices webinar with [Cloudify](http://getcloudify.org/)!

We were honored to have hundreds of registrations and attendees from a wide range of countries, industries, and companies to discuss microservices, containers, and how to simplify the provisioning of a Kubernetes clusters.

[Click here to view the recording](https://mist-1.wistia.com/medias/96pr1hr1j2), also feel free to [view the deck we presented on SlideShare](http://www.slideshare.net/mistio/moving-from-monolith-to-microservices).

We did receive questions via both the Q&A and the Chat features, and some of the latter were submitted anonymously so if anyone has any still unanswered or additional questions, and/or any feedback, just drop us a line from within your Mist.io account.&nbsp;Also, please connect with us on your favorite social network(s): We’re on [Twitter](https://twitter.com/mist_io), [LinkedIn](https://www.linkedin.com/company/2897510), [Facebook](https://www.facebook.com/mistio-172575929564865/) and [Google+](https://plus.google.com/+MistIo).

More to come soon,

The Mist.io Team

====

Update 10/27/16 8:14 AM PDT:

Additional Q&A

**So the microservices are not started with something like Docker Compose for development?**

We tried setting up a development configuration with Docker Compose about a year ago, but it wasn’t working so great, especially when we had to frequently restart services during dev. Then we tried a single node Kubernetes setup for local development using Vagrant and Virtualbox, which ended up adding up a lot of cognitive and computing load in the dev process. For the time being, we’re doing development in a fat Docker container that has all services running with stable network interfaces. It’s not perfect though, because the container keeps getting fatter. In the meantime, Docker Compose has improved and MiniKube seems to be improving the local Kubernetes experience. We plan to give both of them another shot pretty soon.

**Has anything gone wrong in prod yet? What caused it? How did it get resolved?**

Some celery pods would in rare occasions loose connectivity with RabbitMQ. They were in running state but would not execute their workloads, leading to unreliable system behavior that was very hard to reproduce, because all other pods of the same type were working. After we figured it out, we made sure it won’t happen again by writing a special health check that Kubernetes uses to see if the pod is actually working. Now if it happens again we know that Kubernetes will restart the affected pod.

**How much culture change is required for DevOps to move to microservices?**

That depends on your current culture. If it includes DevOps & CI/CD, then you mostly need more of the same, more streamlined, provided as a service to your entire organization. Also, take some steps to cultivate a microservices/component oriented mindset and know-how across your teams, to help them build stuff that stand on their own as well as together.

**Where do you store the logging for monitoring and auditing?**

In ElasticSearch, which we’re consuming as a service.

**Do you forklift everything or you do opportunistic migration to microservices?**

You can forklift some existing modules into containers and pods but probably not all of them. I think you should be opportunistic in exploiting natural partitions in your existing architecture. Keep your old setup running in parallel with the microservices setup, while you incrementally carve out pieces of your monolith and deploy them as microservices.

**How do you handle spikes in utilizations with Κubrenetes?**

We still have checks that alert us about spikes in case we need to do manual adjustments. We’ve configured our pods to scale when their CPU consumption increases. We’re working on improving the metrics and thresholds that trigger scale up events. Also we’re experimenting with auto-scaling the cluster and we plan to provide this functionality to our users as part of the Kubernetes blueprint, in a vendor agnostic manner.

