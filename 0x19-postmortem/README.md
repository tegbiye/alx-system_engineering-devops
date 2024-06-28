## 0x19-Postmortem
## Nginx likes port 80 (a post-mortem)
The following is the incident report for the Nginx connection 
failure that occurred on June 05, 2024. 
I understand this service issue has impacted 
not running a server for other projects.

### Issue Summary
From 10:30 AM to 4:00 PM EAT, curl requests to the local server I set up on port 80 resulted 
in a connection with refused messages. At its peak, the issue affected 
me not to complete the project I have been working on. The incident caused 
a delay not to complete my assignment on time.
### Timeline
- 11:00 AM: I made the Configuration change and when I test (service nginx status)
- 11:05 AM: Nginx is reloaded (restarted)
- 11:30 AM - 12:00 PM: Curl request fails, and the issue began
- 1:30 PM: After lunch, I continued investigating the issue
- 2:00 PM: After going to the forums and Stackoverflow investigated the issue and identified the root cause
- 2:30 PM: I made a successful configuration change rollback.
- 3:00 PM: Nginx restarts begin
- 4:00 PM: After all the nginx is running and completed the project.
### Root Cause
At 11*:00 AM*, I made a configuration change to the nginx configuration file that specifies the ports that the server listens to. The change specified that the default server only listens to requests made on port 8080. The configuration change was for the project purpose and this contributed to the issue.

At 4*:00 PM*, nginx was reloaded to apply the configuration changes, and a minute later, curl requests on port 80 returned connection failure and then rolled back the configuration change and made changes to the configuration file to listen on port 80. The web server was reloaded to apply the changes, and upon another curl request, the connection was restored, and the expected output was returned by the server.
### Corrective and Preventative Measures
I have taken the following corrective and preventative measures to ensure that similar incidents do not occur in the future:
- I have implemented a note about the case and written all the steps I followed to solve if the same error occurs.
- I have put the  comment in the configuration file about the error
- To correct the issue I have consulted forums, stackoverflow for the similar issue if occurred.
