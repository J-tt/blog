---
layout: post
author: Jett
published: true
title: Investigating Western Australia's Dept. of Health Breach
date: 2020-07-21 18:33:00 +0800
categories: [wa, hack, infosec, opinion, breach, paging]
---
This isn't a complete analysis of the breach, but it's what I picked up from a small dive into the issue.

To help protect the kid's identity, we'll be referring to him as Johnny from now on.

## What the breach was
As you've no doubt picked up, the breach originated from the paging system used by Western Australia's Department of Health.

It contained personal information concerning a significant number of patients, especially relating to COVID test results. The pager was used for communication between departments, far out of bounds of its original purpose, which was simply to alert or convey brief messages around hospitals.

## What I think happened
The information below may not be fully accurate, but I'm fairly confident that it's close to what happened.

### Setting the scene
We have Johhny, a youth who likes to monitor emergency services. He's very much into IT and amateur radio. He has some radio gear, some spare time, and he's looking to further his interest.

### The breach
In my opinion, the breach was heavily the fault of the Department of Health, since they were using an unencrypted paging system that broadcasted the data via a very well known protocol.

Johhny has; through either poking around or just asking the right people, found that the Department of Health uses the aforementioned paging protocol, and finds out that it's quite easy to read.

He sets up a server at his home (or somewhere with a residential connection) to pick up these radio broadcasts (which are coming from an antiquated Vodafone service), and he connects it to the freely available and open-source [PagerMon][Pagermon].

#### A sidenote about paging
The way paging works is a crucial aspect of this breach, so I'll include a little bit about it.

Starting as a system for effectively saying "hey call me", paging evolved to carry full messages, acting almost the same as texting, but with one big difference, how it worked under the hood.

![Pager diagram][pagerdiag]

_Credit: [Explain That Stuff][explainthatstuff]_

Paging works by sending your intended message to everyone, and then each device filters out the messages not intended for it.

So from that explanation, you can clearly see why this was not a hack, but more already publicly available information becoming more accessible.

Coming back to the situation at hand, Johhny now has a live feed of all the pagers going off around the Department of Health, and to make it easier to share and view, **he sets it up so that anyone can access it**.

That last step was the crucial one in this breach, but it did have the upside of revealing this horrific data leak since it's impossible to tell who else was accessing this information.

From my investigation, this website has been up and running for **the past 6 months**.

## Aftermath
9 News picks up a scoop that ["malicious hackers" have infiltrated the Department of Health][9news], and sets a PR wheel in motion, which will hopefully inspire some semblance of change.

Unfortunately, 9 News decided to include screenshots of the page, which quickly lead anyone with some spare time to the website (which is now down). However, the website has been partially cached by Google, so **private information is still being leaked**.

I just hope that Johnny gets what he should; a slap on the wrists, and nothing more.

<hr>
Thanks again to [Arszilla][Arszilla]{:target="_blank"} for helping out with editing!

[Pagermon]:         https://github.com/pagermon/pagermon
[explainthatstuff]: https://www.explainthatstuff.com/howpagerswork.html
[pagerdiag]:        /images/2020-07-21-Dept-Health-Breach/pagerdiag.png
[9news]:            https://www.9news.com.au/national/coronavirus-western-australia-wa-data-breach-medical-records-personal-information-hackers-website-covid19/0c78b0c4-29b1-423a-b39d-735841b203ef
[Arszilla]:         https://twitter.com/Arszilla
