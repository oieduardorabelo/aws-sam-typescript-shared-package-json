# AWS SAM TypeScript example using a single package.json to all lambda handlers

Based on GitHub Issue: https://github.com/aws/aws-sam-cli/issues/4832

This repository is an example of how to use a single `package.json` to manage all lambda handlers.

## How it works

Setting `CodeUri` to root folder (`./`) of the stack might cause other issues with other commands. The suggestion is to still point `CodeUri` to a folder with a `package.json` file.

Because of that, we need 2 `package.json` file:

-   **./package.json:** Used to install development dependencies like lint, test and utilities for the management of the project.
-   **./functions/package.json:** Used to install production dependencies for each lambda handler (e.g. aws-sdk, npm modules used by the lambda handler).

Using this approach, we need to run `npm install` in two places. One for the root folder and another for the `functions` folder.
