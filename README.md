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

Organizations and MCommunity groups are a 1:1 correspondence. All members of
the group are added as admins of the organization, and anyone not in the group
will have their admin role removed.

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
