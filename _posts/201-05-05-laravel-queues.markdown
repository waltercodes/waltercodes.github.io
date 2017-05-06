---
layout: post
title:  "Laravel Queues"
date:   2017-05-05 19:22:24 -0600
permalink: /:year/:month/:day/laravel-queues/
---
We were running into an issue a little while ago with file uploads. The file upload would complete successfully in the majority of cases, but some of the post-processing would frequently fail. There was no mechanism for retrying in case of a failure and we also wanted to move the post-processing out of the user's way. I won the lottery and was chosen to implement a [Laravel Queue](https://laravel.com/docs/master/queues) to solve the problem. When you queue a job rather than running the code as part of the upload request, you free the user from waiting for a long and/or unreliable process. You also buy yourself the ability to easily try again when the unreliable part (in this case, an external system) fails.

This week we deployed the new queue logic along with an additional queue -- it runs a type of job that reaches out to a new external service we just barely added into our flow. Queues are so very magical for handling logic that takes a long time or fails occasionally.
