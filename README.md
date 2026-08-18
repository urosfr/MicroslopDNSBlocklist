# Update Your Hosts File

Blocks trackers and junk at the DNS level. One command, done.

## Windows

1. Open **PowerShell as Administrator**.
2. Run:
   ```powershell
   Invoke-WebRequest -Uri "https://raw.githubusercontent.com/urosfr/MicroslopDNSBlocklist/master/hosts" -OutFile "$env:WinDir\System32\drivers\etc\hosts"
   ipconfig /flushdns
   ```

## If You Don't Have Write Permission

Some setups lock the hosts file even for admins. Take ownership and grant write access first, then run the download.

1. Open **PowerShell as Administrator**.
2. Run:
   ```powershell
   takeown /f "$env:WinDir\System32\drivers\etc\hosts"
   icacls "$env:WinDir\System32\drivers\etc\hosts" /grant "$($env:USERNAME):F"
   Invoke-WebRequest -Uri "https://raw.githubusercontent.com/urosfr/MicroslopDNSBlocklist/master/hosts" -OutFile "$env:WinDir\System32\drivers\etc\hosts"
   ipconfig /flushdns
   ```

## Notes

- These commands **overwrite** your current hosts file. If you want a backup first, copy the existing file before running the download command: `copy %WinDir%\System32\drivers\etc\hosts %WinDir%\System32\drivers\etc\hosts.bak`
- Admin privileges are required since the file is in a protected system directory.