---
layout: post
title: "The Story of Station Updates"
date: 2019-11-02 13:47 +0000
categories: post
tag: Trains
---

In June 2019, I started a project to investigate the Realtime Trains (RTT) api. I used python as that was the language I was most proficient in. It was initially just a small file getting a station's departures and displaying them.

I then thought: "Why not create an account to tweet this?" - so I did. Still just a short programme running on my raspberry pi, [@SDY\_Updates](http://twitter.com/sdy_updates) was born. I then added other stations I used frequently: [Bedford](http://twitter.com/bdm_updates), [Stevenage](http://twitter.com/svg_updates) and [St Neots](http://twitter.com/sno_updates). [St Pancras](http://twitter.com/stp_updates), [Finsbury Park](http://twitter.com/fpk_updates) and [Kings Cross](http://twitter.com/kingsx_updates) followed quickly afterwards.

It was at this point that I realised that the RTT api wasn't handling delays very well. I had known about the National Rail Enquiries (NRE) previously and added that into the code, getting the delay data from there. I then realised that I should just use the NRE api rather than combining them.

There followed the first major rewrite of the code to use the data entirley from NRE. It was at this point my raspberry pi was starting to struggle. I first heard about [Linode](https://www.linode.com/?r=a858c9efe4db01c0f0a1d183fff475c7df148b57) in ad on the [Material podcast](http://relay.fm/material). 4 free months was the offer so I took it.

Using [PuTTY](http://putty.org) I transfered the code into a linode running Debian (the same software as the Pi) and with a bit of tinkering, it worked! At this point the project had grown from much more than a python script returning the next departures and needed another rewrite.

Rewrite done, I added [Holyhead](http://twitter.com/hhd_updates) and [Peterborough](http://twitter.com/pbo_updates) and was able to leave it alone to just run.

But I couldn't manage it.

I added [Huntingdon](http://twitter.com/hun_updates) and [Deal](http://twitter.com/dea_updates) and created a master account [@StationUpdates](http://twitter.com/stationupdates). But I then wanted to make all of the station account retweet anything that it tweeted.

After an evening of googling and reading the twitter api documentation I had it implemented and working. But I believe this must have triggered some sort of alert in the back end of twitter.

Twitter started locking the accounts and I'd have to go through and unlock them again. I also lost access to the email for the Bedford account when I reset my phone which meant I couldn't reset the password. The final nail in the coffin was when I wasn't able to recieve the texts twitter sent to unlock the accounts.

So after 5 months of enjoyable tinkering, it has become more stress than fun. So after I've posted this, I'm going to go to the linode console and turn off the server. I've learnt many things working on this project, including when it's right to stop.

If you've followed the accounts and found them useful, I'm sorry. But I feel this is the right choice for me right now. Something you might be interested in is [livedepartures.info](http://livedepartures.info) which I have running on an old tablet giving me 'at station like' information. Or [UK Departure Boards](https://ukdepartureboards.co.uk/) who produce custom departure boards that you can have in your home.

There are a number of people I should thank for their work in enabling this project:

*   The team behind the [requests](https://pypi.org/project/requests/) python module
*   [@ryanmcgrath](https://twitter.com/ryanmcgrath) and [@mikehelmick](https://twitter.com/mikehelmick) the developers of the [twython](https://pypi.org/project/twython/) module
*   [Robert Clarke](https://github.com/robert-b-clarke) the developer of the [nre-darwin-py](https://pypi.org/project/nre-darwin-py/) module
*   [@swlines](http://twitter.com/swlines) the person behind [Realtime Trains](https://www.realtimetrains.co.uk/)

See you around internet