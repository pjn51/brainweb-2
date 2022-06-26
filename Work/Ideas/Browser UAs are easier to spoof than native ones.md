*Browser UAs are easier to spoof than native ones.* When grading sessions for [[My Atos workflow]], I should differentiate between the trustworthiness of user agents that are active on a native app, meaning something built-in to the device, or if they're on a browser.

UAs in a browser are a lot easier to falsify than ones operating on a native app, so the latter is a better indicator of authenticity. 

#idea/compsci/infosec

---
```dataview
LIST
FROM [[Browser UAs are easier to spoof than native ones]] AND -outgoing([[Browser UAs are easier to spoof than native ones]])
```