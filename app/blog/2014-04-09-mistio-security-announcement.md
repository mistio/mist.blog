---
layout: post
title: Mist.io Security Announcement
date: '2014-04-09T21:48:00+03:00'
tags: []
tumblr_url: https://blog.mist.io/post/82212504866/mistio-security-announcement
---
A vulnerability called Heartbleed was exposed in OpenSSL, an open source library that’s responsible for encrypting data over HTTPS for much of the web. Our infrastructure team responded immediately to the exploit and our service was secured in less than 24 hours. We have upgraded to the patched version of OpenSSL, reissued our certificates and resetted all sessions.

Mist.io is no longer vulnerable to this exploit. There is no indication that any Mist.io properties have been breached or that any of our user data has been leaked. Nevertheless, we are taking this threat very seriously and we’re monitoring the situation closely.  
  
We strongly advise our users to change their passwords and reset their cloud providers’ API keys. Also, make sure to upgrade your servers to the latest OpenSSL version and reissue your certificates to ensure that your services are not vulnerable to the exploit.  
  
You can read more about the bug and how to patch it on [heartbleed.com](http://heartbleed.com/)  
  
If you have any questions or concerns, please email us directly at [support@mist.io](mailto:support@mist.io)

