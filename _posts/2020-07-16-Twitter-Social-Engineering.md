---
layout: post
author: Jett
published: true
title: Twitter's Account Takeover Disaster
date: 2020-07-16 22:12:00 +0800
categories: [twitter, hack, infosec, opinion]
---

For those out of the loop, Twitter has just had a very, very, very bad day.


At time of writing they haven't given an official post mortem, something that will *definitely* be needed for them to regain even an ounce of trust from their users, most of which already dislike the platform. Twitter has demonstrated what most people who work in the industry already know: your security is only as strong as your staff, whether that be your developers or, in Twitter's case, your support team.


![XKCD 2030](https://imgs.xkcd.com/comics/voting_software.png){:class="img-responsive"}

_([source](https://xkcd.com/2030/))_


# So what actually happened? (The short version)

The summary of the facts as they stand is this:

1. A bunch of high profile celebrity accounts advertised a Bitcoin scam (in this case "Send me your money and I'll send twice as much back")
2. A selection of people fell for it, netting the scammers who'd broken into the accounts roughly 110k USD (I'll come back to this, don't worry)
3. Twitter support took a few hours to actually shut the whole thing down (and was still cleaning up for awhile after that)
4. Vice managed to get in touch with the "hackers" who revealed that a Twitter employee gave them access


# How'd they do it?

The answer is rather underwhelming, they bribed/social engineered a Twitter employee to hand over their God mode staff account.

Yep, that's it.

From there they reset emails, disabled 2 factor authentication, and waltzed in the front door.


<blockquote class="twitter-tweet"><p lang="en" dir="ltr">We detected what we believe to be a coordinated social engineering attack by people who successfully targeted some of our employees with access to internal systems and tools.</p>&mdash; Twitter Support (@TwitterSupport) <a href="https://twitter.com/TwitterSupport/status/1283591846464233474?ref_src=twsrc%5Etfw">July 16, 2020</a></blockquote> 

The above Tweet ([direct link](https://twitter.com/TwitterSupport/status/1283591846464233474)) is a bit at ends with Vice's article, which states the following:

> "We used a rep that literally done all the work for us," one of the sources told Motherboard.

_[source](https://www.vice.com/en_us/article/jgxd3d/twitter-insider-access-panel-account-hacks-biden-uber-bezos)_

The difference in stories is to be expected, at this stage there is most likely a PR firm consuming coffee by the litre planning out how to respond to this while the engineers at Twitter desperately try to fulfill the claims of the aforementioned PR firm.

While the above is speculation there is one thing for sure:

**Not much sleep is being had, and a lot of very important decisions are being made very quickly.**

It's the crucial first response of a security incident that sets the tone for the response down the track.


# The fallout and some speculation

The fallout for this event is hard to gauge, and it's going to be hard to see clearly for some time.


Immediately, it stirred a bit in US politics, with a Republican senator contacting Twitter to ask if Donald Trumps account was affected. The fact that it wasn't might come as a surprise, given the potential for mayhem. This caused many to point fingers at Russia, which would've been potential if there wasn't now additional protections due to a Twitter staff member deleting Trump's account in November 2017. 

But, despite Twitter's protection on Trump, ex-presidential candidate Mike Bloomberg was also affected, showing that the protections only extened so far (my guess is just Trump and Twitter's CEO). The lack of protection from impersonation will most likely spur further govermental inquiry into how Twitter handles security, which may culminate in Twitter CEO Jack Dorsey being dragged in front of Congress once more.

But, while politics may be interesting...

The biggest and most interesting part of the fallout will be learning the motivation behind the Bitcoin scam:

Did someone social engineer a Twitter employee to scam money with one of the most basic moves you can pull

Or

**Was it a smokescreen for harvesting DMs/Private Info/Whatever?**

Within the infosec (read: computer security nerds) community there's a large amount of surprise and questioning of why someone with the golden ticket to Twitter's systems would leverage it on a Bitcoin scam like they did, which would be a headache to cash out properly.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">It&#39;s like managing to sneak into Fort Knox and then running off after stuffing your pockets full of quarters</p>&mdash; Pwn All The Things (@pwnallthethings) <a href="https://twitter.com/pwnallthethings/status/1283719083175882755?ref_src=twsrc%5Etfw">July 16, 2020</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

The attack makes even less sense when you consider the difficulty in laundering large amounts of Bitcoin, there are services which do it for you, but it gets harder to hide the more you have. 

To further illustrate why this is difficult, it's been leaked that the FBI closely monitor funds moving around the very publicly viewable Bitcoin network ([source](https://decrypt.co/34740/blueleaks-how-the-fbi-tracks-bitcoin-laundering-on-the-dark-web)). If the hackers are US based, they're looking to be in a world of hurt, especially with no way to easily flee the country in the current pandemic. 

In fact, some people so strongly believed that Bitcoin was a poor choice they chose to send the attackers messages in the form of sending them money via specially crafted Bitcoin addresses:

```
1JustReadALL1111111111111114ptkoK 0.00000666 BTC
1TransactionoutputsAsTexta13AtQyk 0.00000667 BTC
1YouTakeRiskWhenUseBitcoin11cGozM 0.00000668 BTC
1forYourTwitterGame111111112XNLpa 0.00000669 BTC
1BitcoinisTraceabLe1111111ZvyqNWW 0.00000670 BTC
1WhyNotMonero777777777777a14A99D8 0.00000671 BTC
```

Translation: "Just read all transaction outputs as text. You take [a] risk when you use Bitcoin for your Twitter game. Bitcoin is traceable. Why not Monero[?]"

([Monero](https://en.wikipedia.org/wiki/Monero_%28cryptocurrency%29) is another cryptocurrency, which focuses more on privacy)

[Source for transaction data](https://www.blockchain.com/btc/tx/67b814526ae6ee78a16059bfcfc06ed7768c92c58f3409367cb180627631ddbe).

<hr>

A final interesting bit of note is the presence of a "search blacklist" button on the leaked Twitter screenshots within the Vice article. this backs up Vice's claims that Twitter is "shadowbanning" users on the platform (see [this](https://www.nytimes.com/2018/07/26/us/politics/twitter-shadowbanning.html) NY Times article). This bit of note was pointed out to me by a coworker, so I have to give them credit in spotting it.


To add further weight to this, not only did Twitter vehemently deny the claim, they did so **[in front of congress](https://www.vox.com/2018/9/6/17824652/twitter-dorsey-energy-and-commerce-hearing-shadow-banning)** (see also, [The Verge's coverage](https://www.theverge.com/2018/7/27/17620194/twitter-shadow-ban-trump-conservatives-search-results)).

I have to admit, this casts doubt in my mind on the authenticity of the screenshots provided by Vice, which got shredded in the linked articles. The UI for the moderation tools also clash with Twitter's design philosophy slightly, but that could just be lack of polish on an internal tool.

All in all, I'm left with many burning questions, sadly few of which I anticipate recieving a sound answer to.

