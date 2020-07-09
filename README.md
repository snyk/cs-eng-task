# Customer Success Task

## Installation

1. If you have `git` available, you can clone this repo:
   ```
   git clone git@github.com:snyk/cs-eng-task.git
   ```

   Otherwise, please [download it](https://github.com/snyk/cs-eng-task/archive/master.zip) to your machine.

2. [Install Node](https://nodejs.org/en/download/) if you don't have it already

3. Install dependencies
   ```
   npm install
   ```

## Running the tests

```
npm test
```

## Exercise

This repo is a simplified version of our system that handles user logins and ensures that they get access to the correct groups.

In this exercise we want you to update an existing login handler called `src/login-handlers/adfs-acme.js`. Currently the handler makes sure that users which have the string `snyk-admin` in the array found at `profile._json.groups` get made into group admins.

We want you to modify this script so that users with the string `snyk-read-only` in the array found at `profile._json.groups` get made into group read-only users. This is achieved by ensuring that the function returns an object with `addAsGroupReadOnly` set to an array of groups for which they should be a read only user.

Consider testing this new functionality.

## Extension Activity (time permitting)

If you achieved that first task and want an extension activity, keep reading!

We now want you to handle a new customer, called "Hooli" and ensure that when someone logs in we apply the following logic via a new login handler:
- If they have `snyk-admin-group1` then they should be an admin of the group named `hooli-group1`.
- If they have `snyk-admin-group2` then they should be an admin of the group named `hooli-group2`.
- If they have `snyk-read-only-group1` then they should be a read only user of the group named `hooli-group1`.
- If they have `snyk-read-only-group2` then they should be a read only user of the group named `hooli-group2`.

If a user logs in and has _both_ `snyk-*-group1` _and_ `snyk-*-group2`, make sure they're added to both Groups with the appropriate role.

Write some tests for this new login handler.
