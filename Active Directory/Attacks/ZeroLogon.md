Dangerous bug, proceed with caution.
We're basically setting the password for the domain controller to `null`
- If we don't reset the password, we will break the controller
Thankfully, we can also just check if the domain is vulnerable to this: https://github.com/SecuraBV/CVE-2020-1472
POC: https://github.com/dirkjanm/CVE-2020-1472