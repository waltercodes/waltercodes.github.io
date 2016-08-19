---
layout: post
title:  "Revisionable"
date:   2016-04-03 20:51:24 -0600
permalink: /:year/:month/:day/revisionable/
---
This week I've had the pleasure to explore [Revisionable](https://packagist.org/packages/venturecraft/revisionable). Revisionable is a package that automatically creates a history of modifications to your [Eloquent](https://laravel.com/docs/master/eloquent) models. One of my projects could really use an easy way to track down the changes and explain how each record got to its current state. This package seems like a good choice.

Revisionable change records include the id of the user that made the change, which won't work if you use an authentication system that doesn't point to a single model. Luckily, if all of your models inherit from a base model, you can just override getUserId() in the base model with your own logic for getting the ID of the active user. This simple approach will work if you only need to attribute changes to one type of user (e.g. Admin users).

You can retrieve the history using methods that are provided by the Revisionable trait, which you attach to any models you want to track. I'm excited to start using this in my project.
