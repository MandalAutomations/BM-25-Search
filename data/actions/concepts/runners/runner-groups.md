# Runner groups

Learn about what a runner group is, and how to use them to control access to runners at the organization level.

## About runner groups

To control access to runners at the organization level, organizations using the GitHub Team plan can use runner groups. Runner groups are used to collect sets of runners and create a security boundary around them.

When you grant access to a runner group, you can see the runner group listed in the organization's runner settings. Optionally, you can assign additional granular repository access policies to the runner group.

When new runners are created, they are automatically assigned to the default group unless otherwise specified. Runners can only be in one group at a time. You can move runners from one runner group to another.

## Next steps

To learn how to use runner groups to control access to larger runners, see [Controlling access to larger runners](/en/actions/how-tos/using-larger-runners/controlling-access-to-larger-runners).

For information on how to route jobs to runners in a specific group, see [Choosing the runner for a job](/en/actions/using-jobs/choosing-the-runner-for-a-job#choosing-runners-in-a-group).