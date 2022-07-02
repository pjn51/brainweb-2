# DREMR training
on [[22-06-28 Tue]]
with [[Andrew]]

---
In this meeting, Andrew and I went over [[DREMR]], the "Dradis Email Relay" tool. This tool allows us to see the communications between employers and jobseekers. We discussed why this tool exists, when we use it, and some other stuff, based on a slide deck. ^1

The reason that we use this tool is to make sure communications are appropriate, and as a way of adding insight to account-level moderation. Moderators always check DREMR during account-level moderation.

Additionally, jobseekers can report individual messages, so DREMR reports that as well. This sort of taps into the [[Report A Job|RAJ]] functionality. 

When messages trip existing rules created in [[Rulebook]], they automatically get withheld from the jobseeker and the account goes into the moderation queue. 

Note that this tool is confidential, and should not be shared with user-facing teams. 

I asked where the [[data]] can be accessed, and Andrew explained that there are a few [[IQL indices]] such as `dremrrelay`, `dremrmsg`, and `mmsMessageRelayDecision`. The latter index is the source of the rules that messages must clear before reaching their jobseeker destination.

I also asked if there was any attempt to automate rule creation. He said that yes, there is a third-party tool called Mailgun, but it isn't very reliable. He said that this process is riddled with easy-to-fix bugs and issues that the DREMR team has been asked to fix for years, but hasn't. He seemed rather frustrated that a lot of loopholes could be easily closed, but for some reason they haven't been. He showed me a ticket related to Brazilian scam issues that has a ton of links, indicating that it's been an outstanding issue for years.

Andrew referred me to a more technical slide deck so that I could learn some of the more specific techy stuff about what's going on under the hood. ^2

---
1. [Slide deck](https://www.google.com/url?q=https://docs.google.com/presentation/d/1zuIytqEkwZcPkePs3MOqvYj4uDDHgW1PqT3tfRRPjdY/edit%23slide%3Did.g10e11801d35_0_0&sa=D&source=calendar&ust=1656421992008918&usg=AOvVaw1YIg2nUcYEEk_exL3B65wo)
2. [Technical slide deck](https://docs.google.com/presentation/d/1U1M8jGtASZEc45jpg-A8b4fQGWSL0jNnpLq9N_jJDRs/edit#slide=id.gd06532fa8d_0_68)