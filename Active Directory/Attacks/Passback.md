We can't lab this one very well
Target: Something that connects to LDAP or SMB
- Printer
- Phone
- Whatever
Have the device point to your computer and eventually you'll get creds for that SMB/LDAP service account that the printer/phone/whatever uses to connect to the domain.
- `nc` to listen
- `responder` to listen too
It will just send over the creds in cleartext
Never count out the Passback
https://www.mindpointgroup.com/blog/how-to-hack-through-a-pass-back-attack