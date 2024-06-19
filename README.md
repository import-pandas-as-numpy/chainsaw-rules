# chainsaw-rules

A set of custom Chainsaw rules for event log threat hunting.

## Usage

```bash
chainsaw hunt -r chainsaw-rules/rules .
```

There is a redundant rule in here, `network_login_aggregate`. This simply collapses down network logins into a digestable
summary for at-a-glance analysis. Keep this in mind when running this in conjunction with the defualt ruleset
of Chainsaw, as it will duplicate entries.
