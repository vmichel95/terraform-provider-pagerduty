---
layout: "pagerduty"
page_title: "PagerDuty: pagerduty_team"
sidebar_current: "docs-pagerduty-resource-team"
description: |-
  Creates and manages a team in PagerDuty.
---

# pagerduty\_team

A [team](https://v2.developer.pagerduty.com/v2/page/api-reference#!/Teams/get_teams) is a collection of users and escalation policies that represent a group of people within an organization.

The account must have the `teams` ability to use the following resource.

## Example Usage

```hcl
resource "pagerduty_team" "parent" {
  name        = "Product Development"
  description = "Product and Engineering"
}

resource "pagerduty_team" "example" {
  name        = "Engineering"
  description = "All engineering"
  parent      = pagerduty.team.id
}
```

## Argument Reference

The following arguments are supported:

  * `name` - (Required) The name of the group.
  * `description` - (Optional) A human-friendly description of the team.
    If not set, a placeholder of "Managed by Terraform" will be set.
  * `parent` - (Optional) ID of the parent team. This is available to accounts with the Team Hierarchy feature enabled. Please contact your account manager for more information.

## Attributes Reference

The following attributes are exported:

  * `id` - The ID of the team.
  * `html_url` - URL at which the entity is uniquely displayed in the Web app

## Import

Teams can be imported using the `id`, e.g.

```
$ terraform import pagerduty_team.main PLBP09X
```
