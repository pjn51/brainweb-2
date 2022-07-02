# IQL overview
on [[22-06-30 Thu]]
with [[Lynn]]

---
In this freewheeling meeting, Lynn walked me through some interesting IQL queries, and a list of all IQL functions ^1-2

She also imparted some [[IQL]] tips: when selecting [[data]] FROM multiple [[IQL indices]], we have to put the date range after the first one. 

I also asked why so many people on the team seem to use Firefox, and she said it was because their hotkeys are better than Chrome. Interesting.

Getting back on track, we discuseed how relative dates such as `today` become absolute (`2022-06-30`) after the query runs, but there is a way to prevent this when sharing a query.

She showed me idash, a newer IQL webapp that allows saving queries. She doesn't like it since it isn't responsive to screen size.

Lynn also told me about her current project, Project One to One. They're attempting to find companies that are posting the same job multiple times in order to abuse the [[SERP]] ranking system and get more views on their job. This seemed like an interesting problem to me, since it would be kind of hard to sniff out the evasion tactics that one could do, such as changing the location, title, or description slightly.

---
1. [Useful IQL queries gdoc](https://docs.google.com/document/d/1Ze9g60WJ-aATSOIt7sJ27MCfwB1ZdVxePgTpsljfn8w/edit)
2. [Confluence doc on all IQL functions](https://wiki.indeed.com/display/IQL/IQL2+-+All+Functions)