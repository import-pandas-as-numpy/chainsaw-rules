# chainsaw-rules

A set of custom Chainsaw rules for event log threat hunting.

## Usage

```bash
chainsaw hunt -r chainsaw-rules/rules .
```

There is a redundant rule in here, `network_login_aggregate`. This simply collapses down network logins into a digestable
summary for at-a-glance analysis. Keep this in mind when running this in conjunction with the default ruleset
of Chainsaw, as it will duplicate entries.

### Rules

#### MSSQL Failed Login

Aggregate failed login attempts via MSSQL. For some reason, Chainsaw refuses to coalesce the Client field,
aggregation can be disabled if you want to know where login bruteforcing is coming from specifically, but
given the volume of bruteforcing that tends to be observed, it's best left aggregated by default.

#### XP Cmdshell

Actiivty relating to the `xp_cmdshell` functionality on MSSQL. This adds a decent at-a-glance
but further log diving will be necessary to determine the actual commands invoked via xp_cmdshell
if they are not apparent through other event logs.

#### ScreenConnect

Timeline ScreenConnect connections.

#### RMM Enum

Modified RMM enumeration rule from the default Chainsaw rulset. Focused on simply detecting arbitrary RMM
usage for at-a-glance statistics.
