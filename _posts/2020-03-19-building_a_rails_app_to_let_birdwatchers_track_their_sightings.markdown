---
layout: post
title:      "Building a Rails app to let Birdwatchers track their sightings"
date:       2020-03-19 13:52:48 -0400
permalink:  building_a_rails_app_to_let_birdwatchers_track_their_sightings
---


For my Rails porfolio project, I made an app that allows a user, a birdwatcher, to create sightings of birds and keep track of them. The first thing to do, as always, is to build a signup/login/logout system.

Signup isn't too difficult, just direct the user to birdwatcher#new which renders a partial shared with birdwatcher#edit which, if accurate, will be saved to the database, the session[:birdwatcher_id] will be set to the current user's id, and the user will be redirected to birdwatcher#show.

Logging in and out is roughly the same, save for a few caveats; we need to find and authenticate the user on an appropriate login and give them a generic error message on an inappropriate login. Logout is simply just clearing the session hash and redirecting the user to the home page.

The most difficult part of all of this was the requirement to allow users to login from other websites via omniauth and a specialized omniauth gem to pair with the site. For my project, I chose to allow users to login from GitHub. Once you decide to use a site, you have to go to the site's developer section and make an app in order to get a client_id and a client_secret, which have to be stored in a local .env file along with having the dotenv gem for rails. But once you get everything set up properly and you manage to identify the appropriate elements to input into your database, it's just a regular login from there.

Next, after you can make, and edit and delete, birdwatchers, you have to make birds for them to watch. Right now, the user can, on signup or when editing their profile, identify themselves as an ornithologist which will allow them access to bird#new which lets them create a bird object with :common_name, :scientific_name, and :conservation_status.
Now that we have birds and birdwatchers, we can create sightings (birdwatchers have many sightings and have many birds through sightings, and vice versa; sightings belong to birds and birdwatchers). All sighting routes, except sighting#index are nested under birdwatchers so all sightings will be associated to their birdwatcher. 

Lastly, the birdwatcher#index page sorts birdwatchers into ornithologists and casual birdwatchers by way of scope functions.
