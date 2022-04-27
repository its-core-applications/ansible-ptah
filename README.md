# ptah

ptah provisions Ansible Tower organizations, teams, and users based on
public MCommunity groups.

## Superadmins

In the config, `admins` is a list of groups whose members are given full control
of the Tower instance.

```yaml
admins:
  - blackops
  - its email operations
```

## Organizations

`organizations` is a mapping of organization names. Note the trailing
colon (`:`) for empty values.

```yaml
organizations:
  flowerysong:
```

All members of the group that the organization is named after are
automatically added as admins of the organization.

Additional admin groups can also be configured:
```yaml
organizations:
  flowerysong:
    admins:
      - blackops
```

Any organization admin that is no longer in a configured MCommunity group
will be removed.

For delegating access to people outside the main group, teams can also be
configured within each organization.

```yaml
organizations:
  blackops:
    teams:
      flowerysong:
```

Membership of the team will be kept in sync with the MCommunity group, and
organization admins can manually delegate access to the team.
