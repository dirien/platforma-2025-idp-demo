# Golden AI Path: Static Website on AWS S3

## Background

This Golden Path creates a static website on AWS S3 with the help of a Pulumi blueprint. It will execute different agents for the specific tasks.

## Implementation Instructions

### Prerequisites

Delete folder `/tmp/mcp/static-website-s3-aws-typescript/` and `/tmp/mcp/blueprints`

### Steps
1. GitHub Agent
   1.1 The `github_agent`  clones `https://github.com/dirien/blueprints` and copy the folder  `static-website-s3-aws-typescript` to  `/tmp/mcp/`.

   1.2 Then create a `/tmp/mcp/static-website-s3-aws-typescript/Pulumi.dev.yaml` file with following content:
   ```yaml
   environment:
   - pulumi-ultimate-gitops/dev
   ```

   Use the default values for the config values in the `/tmp/mcp/static-website-s3-aws-typescript/Pulumi.yaml` file under the `tag`
   ```yaml
   template:
     config:
   ```

   Append the results in the `/tmp/mcp/static-website-s3-aws-typescript/Pulumi.dev.yaml` in the format:
   ```yaml
   config:
    key: <value>
   ```
   1.4 Replace the content of the `div`-tag with the `class="starter-template"` with this large title: "Hello PlatforMA 2025" in the file `/tmp/mcp/static-website-s3-aws-typescript/html/index.html`
   1.5 Now run the command `npm install` in the `/tmp/mcp/static-website-s3-aws-typescript/` folder.

   1.6 Check that following folder exist:
   - `/tmp/mcp/static-website-s3-aws-typescript/`

   1.7  Check that the following files exist:
   - `/tmp/mcp/static-website-s3-aws-typescript/Pulumi.dev.yaml`
   - `/tmp/mcp/static-website-s3-aws-typescript/node_modules`

   1.8 After this the `github_agent` the task is done and report back to the `supervisor`
2. Pulumi Agent
   1.1 Switch to the `pulumi_agent` and call first `pulumi preview` for the details and proper flag usage of the commend

   1.2 Then run a `pulumi preview` with the stackname `dirien/static-website-s3-aws-typescript/dev` and the workdir `/tmp/mcp/static-website-s3-aws-typescript/`

   1.3 If there is an error in the `pulumi preview` stop and return  
   1.4 Now call `pulumi up` and skip user interaction with the flags `-y -f`
   1.5 Get the URL from the Pulumi output and return this to the supervisor to display to the user
   1.6 After this the `pulumi_agent` is done and report back to the `supervisor`

### Wrap-up
Communicate the status clearly to the user and return the website URL
