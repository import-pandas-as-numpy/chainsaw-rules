# chainsaw-rules

A set of custom Chainsaw rules for event log threat hunting. These aren't intended to stand alone for
event log analysis, but are intended to operate ad-hoc side by side the chainsaw default ruleset. This
stance may change in the future, as I'm able to rewrite certain default rules into something that I believe
is a little more ergonomic for at-scale analysis.

## Usage

```bash
chainsaw hunt -r chainsaw-rules/rules .
```

There is a redundant rule in here, `network_login_aggregate`. This simply collapses down network logins into a digestable
summary for at-a-glance analysis. Keep this in mind when running this in conjunction with the default ruleset
of Chainsaw, as it will duplicate entries.

## Disabled Rules

Several default rules in this ruleset have a `tautology` conditional statement. 
This is designed to *always* evaluate to false, thus disabling the rule. If you need to use
a rule that is present in the default ruleset and it is disabled, you can remove the 'tautology'
condition, which will cause the rule to function as anticipated. 

This was done to reduce verbosity for rules that I don't consider wildly useful in day-to-day triaging
and can create a large amount of output volume.
