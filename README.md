# BeFit

BeFit is an ASP.NET Core MVC application for tracking exercises and training sessions.

This repository is a mirror of the current local workspace. Below are the minimal steps to run the project locally.

How to run (short)

PowerShell (from the workspace root):

```powershell
Set-Location -Path "C:\Users\enesy\Desktop\BeFit-app"
# Option A: run on an explicit port (recommended so it does not conflict with other apps)
$env:ASPNETCORE_URLS = "http://localhost:5005"
dotnet run --project "BeFit\BeFit\BeFit.csproj" --no-launch-profile --configuration Debug

# Then open in your browser: http://localhost:5005/

# Option B: run with the default settings and open the URL printed by dotnet
dotnet run --project "BeFit\BeFit\BeFit.csproj"
```

Stop the running app by finding its PID and stopping it, for example:

```powershell
Get-CimInstance Win32_Process | Where-Object { $_.CommandLine -match 'BeFit\\BeFit\\BeFit.csproj' } | Select-Object ProcessId, CommandLine
Stop-Process -Id <pid>
```

Notes
- If you use port 5005 make sure it's free (no other service listening). If binding fails because the port is in use, change the port (e.g. 5006) by adjusting `ASPNETCORE_URLS`.
- The local SQLite DB and runtime logs are intentionally ignored in `.gitignore`.

If you want, I can add a GitHub Actions workflow to build this project on every push.
