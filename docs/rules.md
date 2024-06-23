### Hacktools

#### impacket_sysmon.yml

Does a best effort attempt to sus out impacket utilization via Sysmon event logs.
This really only works for the default Impacket arguments, this is a work in progress.

#### susp_PS.yml

This is based off of Florian Roth's Susp_JAB_PS ruleset. Beacons and base64 encoded
reverse shells from revshells will come with 'JAB' as the first portion of the encoded
payload, which shockingly isn't actually that common despite it being a simple dollar sign.

### MSSQL

#### mssql_failed_login.yml

Simply aggregates failed logins on an MSSQL instance, and points back to the client(s) that
may be responsible for those logins.

#### xp_cmdshell.yml

Detects xp_cmdshell usage. This will require drilling down on commands via other logs
as the Windows event logs do not capture command shell arguments directly. That said, the
resulting `cmd.exe` or `powershell.exe` processes that will likely follow should be indicative
enough of malice.

### RMM

#### logmein.yml

Detects successful connections via LogMeIn. This is based off the [RULER project](https://ruler-project.github.io/ruler-project/)
so I don't actually have any event logs for this one to figure out a better way to display this data. Gladly
accepting submissions so I can see how this data is formed, otherwise this should just arbitrarily return some
likely existant data when the document is tagged, which can then be drilled down on.

#### realvnc.yml

Detects successful logins via RealVNC or TightVNC. Again, based on the RULER project, so a stab in the dark.
Once again, should be at least mildly useful at returning some arbitrary information regarding the event, which can
then be drilled down on.

#### rmm_enum.yml

The default RMM detection, but aggregates the services to prevent terminal flooding. Useful for fingerprinting
hosts and the RMM's they might be using (or have installed).

#### screenconnect.yml

Detects connections via ScreenConnect, displays usernames. I believe the --full param should be useful here to
return more granular connection information if desired.

### aspnet_except.yml

Many vuln scanners and tools like sqlmap will raise exceptions in ASP.NET. This query is an attempt to identify
these exceptions.

### network_login_aggregate.yml

The default network login rule, but aggregates logins by the source and username. Useful for at-a-glance information
regarding network logins over a given time period.

### scheduled_task_creation.yml

Does exactly what's on the tin and detects scheduled task creation. This has the potential to be quite noisy depending
on the length of event logs, but plenty of malware achieves persistence via scheduled tasks.
