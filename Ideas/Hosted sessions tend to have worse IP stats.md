*Hosted sessions tend to have worse IP stats.* When I'm grading sessions as a part of [[My Atos workflow]], I should differentiate between the IP stats of a fixed, local IP, and the stats I might see when a user is using a hosting service.

Since hosting service IPs see a ton more traffic than a user's home IP, it's possible that a bad actor could have used that IP for abuse, leading to the IP being automatically blacklisted. 

If that were to happen, we would see `IdsLocked` as the error message for the STGd, but that wouldn't automatically be as bad. In that case, differentiate between the `IPBlock_Action` and the `Lockout_Action` in the details pane of the STG.               
               
#idea/compsci/infosec 

---
```dataview
LIST
FROM [[Hosted sessions tend to have worse IP stats]] AND -outgoing([[Hosted sessions tend to have worse IP stats]])
```