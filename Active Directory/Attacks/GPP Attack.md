AKA cPassword
Group Policy Preferences (GPP) had admins create policies using embedded credentials. These creds were encrypted and placed in "cPassword". Key was released, but was patched in MS14-025.
- If it's been previously used, this will work
- DC is likely patched, but try everything
### Tools:
`gpp-decrypt`
- Built into Kali
- Plug in the cpassword, get result
`metasploit`
- `smb_enum_gpp`
	- You need valid creds, but you can get those

### Recommendations:
- Patch
- Delete old GPP xml in the SYSVOL