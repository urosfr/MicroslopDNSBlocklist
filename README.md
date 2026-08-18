# Update Your Hosts File

Blocks trackers and junk at the DNS level. One command, done.

## Windows

1. Open **PowerShell as Administrator**.
2. Run:
   ```powershell
   Invoke-WebRequest -Uri "https://raw.githubusercontent.com/urosfr/MicroslopDNSBlocklist/master/hosts" -OutFile "$env:WinDir\System32\drivers\etc\hosts"
   ipconfig /flushdns
   ```



## Notes

- These commands **overwrite** your current hosts file. If you want a backup first, copy the existing file before running the download command (e.g. `cp /etc/hosts /etc/hosts.bak` or `copy %WinDir%\System32\drivers\etc\hosts %WinDir%\System32\drivers\etc\hosts.bak`).
- Admin/root privileges are required since the file is in a protected system directory.
