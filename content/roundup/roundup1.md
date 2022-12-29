---
title: "Weekly Roundup #1: December 12-19th 2021"
date: 2021-12-19 
tags: ["Security","Roundup"]
description: "The first roundup!"
draft: false 
---

# What is this?
This is the first of a weekly "round up" that aims to summarize the security or IT related concepts I have worked on this week during my free time. My goal is to create a *footprint* for others to follow in if they so desire. When I was first learning the basics of security I struggled to find projects that I could work on to help me learn useful security practices and techniques. Some weeks will have have more content than others depending on the amount of free time I have.

# 12/12/2021 
- Went over SANS GSEC certification notes
- Spent entirely too long getting [git.grahamhelton.com](http://git.grahamhelton.com) and [twitter.grahamhelton.com](http://twitter.grahamhelton.com) to point to my twitter and github using DNS...
- Rebuilt homelab into a snazzy new case. 

![](/Pasted-image-20211214203659.png)

- Compiled some information about how to get started with docker to go through once I finish my SANS GSEC material

```bash
# Docker learning resources
https://www.youtube.com/watch?v=wCTTHhehJbU

https://www.youtube.com/watch?v=3c-iBn73dDE&feature=youtu.be

https://www.youtube.com/watch?v=MnUtHSpcdLQ&feature=youtu.be
```

# 12/13/2021 
- Watched Black hills information security's [emergency log4j webcast](https://www.youtube.com/watch?v=igoDXnkYDy8)
- Studied SANS GSEC notes
- Spent forever researching [searx](https://searx.github.io/searx/) and borking installs.
- Fiddled with my [recipe website](https://level99cooking.com) to fix some formatting issues. 

# 12/14/2021
- Studied SANS GSEC notes
- Fixed searx install from previous day
- Wrote [Thou Shall Not Snoop Our Searches - Searx Installation and Discussion](https://www.grahamhelton.com/blog/searx/)
- Added some android VMs to my lab for future projects

# 12/15/2021
- Discovered [Unsupervised Learning](https://danielmiessler.com/podcast/) by [Daniel Miessler](https://twitter.com/DanielMiessler)
- Watched [A Tale of Two Johns (John hammond and John strand interview)](https://www.youtube.com/watch?v=7LXfBSuaFFE)
- Set up rsyslog server in my home lab via [this tutorial](https://www.techrepublic.com/article/how-to-install-and-configure-rsyslog-for-a-centralized-linux-log-server/) (This was very easy)
	- Noticed some weird things going on in my network. The first being some very strange pings every few minutes to some random IPs. After some researching I found a reddit post where someone described the same problem. Looks like its a part of [PIA's code](https://github.com/pia-foss/desktop/blob/master/daemon/src/latencytracker.cpp#L64-L101) to check the latency to their servers.
	
	![](/Pasted-image-20211215161851.png)
	
	- Noticed UFW was blocking some more traffic  that happened to beacon every 2 minutes and 6 seconds... 
 ![](/Pasted-image-20211215162540.png)
 - Investigated further with wireshark and found out it was an IGMP query packet to refresh the IPs of multicast group memberships. This was sent out by my router. 
 ```bash
sudo tcpdump -i <interface> -s 65535 -w sketchy.pcap
 ```
 
 - Added [pushRsyslog.sh](https://github.com/grahamhelton/smallscripts/blob/main/pushRsyslog.sh) to my [smallScripts github repot](https://github.com/grahamhelton/smallscripts)
 
 # 12/16/2021
 - Listened to [The Privacy, Security, and OSINT show](https://www.inteltechniques.com/podcast.html) episodes 242 and 243
 - Discovered [Privacy.sexy](https://privacy.sexy/) which is a collection of scripts to disable windows / mac features that reduce privacy 
 - Verified with PIA VPN that they do send out pings to all their servers every couple minutes to "verify connectivity" (This still makes me feel uneasy...)
 
![](/Pasted-image-20211219153745.png)

 - Went over GSEC notes.
 
 # 12/17/2021
 - Studied GSEC
 	- Finished indexing GSEC books
 - Formally accepted the agreement for the SANS Masters degree program (🎉 🎉🎉)
# 12/18/2021
- Got sick :/
- Binged like 20 [John Hammond videos](https://www.youtube.com/c/JohnHammond010) 
 - Learned a little bit about [web3](https://www.youtube.com/watch?v=l44z35vabvA&t), [filecoin](https://docs.filecoin.io/about-filecoin/what-is-filecoin/#for-users), and [IPFS](https://www.youtube.com/watch?v=5Uj6uR3fp-U&t)
 
# 12/19/2021
- Listened to [darknet diaries #106](https://darknetdiaries.com/episode/106/)
- Published this round-up
- Began looking for some open source asset management tool.
	- [@snipeyhead](https://twitter.com/snipeyhead) on twitter linked me to [snipe-it](https://snipeitapp.com/)


# Have any questions
Do you have any questions? Feel free to [reach out to me on twitter](http://twitter.grahamhelton.com). See you next Sunday. :)
