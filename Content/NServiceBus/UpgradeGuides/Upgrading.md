---
title: Upgrading NServiceBus Versions, General Guidance
summary: 'A guide for migrating from one major version to another '
tags:
- Migration
---

***WORK IN PROGRESS***

You will need to do this in 2 steps: 
1st step: 2.6 to 3.3.8 (latest 3.x) 
2nd step: 3.3.8 to 4.x (latest 4.x)

Upgrading 2.6 to 3.3.8:
here are some links:
https://github.com/Particular/NServiceBus/releases/tag/3.3.8
http://www.youtube.com/watch?v=LH0qeienRpg
http://andreasohlund.net/2012/01/27/convention-over-configuration-in-nservicebus-3-0/
http://andreasohlund.net/2012/03/08/nservicebus-3-0/
http://stackoverflow.com/questions/9445915/migration-patch-from-nservicebus-2-6-to-nservicebus-3-0

i would look at also including moving to unobtrusive mode in your upgrade for reduced coupling in your code.

Upgrading 3.x to 4.x it should be relatively straight forward. Take a look here: 
https://github.com/Particular/NServiceBus/releases/tag/4.0.0

Look at: “Compatibility and Upgrades"

[V 4.x to v 5.x](4to5)
