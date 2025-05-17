# Golden AI Path: DigitalOcean Kubernetes Cluster

#### Prepare
Delete folder `/tmp/mcp/do-kubernetes-argocd/` and `/tmp/mcp/blueprints`

#### Supervisor

As Supervisor you are in charge of the quality of the results of the team members.

#### GitHub

##### Steps

1.
The `github_agent` to clone `https://github.com/dirien/blueprints` and copy the folder  `do-kubernetes-argocd` to  `/tmp/mcp/`.

2.
Then create a `/tmp/mcp/do-kubernetes-argocd/Pulumi.dev.yaml` file with following content:

```yaml
environments:
- pulumi-ultimate-gitops/dev
```

Use the default values for the config values in the `Pulumi.yaml` file under the `tag`

```yaml
template:
  config:
```

Append the results in the `Pulumi.dev.yaml` in the format:

```yaml
config:
 key: <value>
```
3.
Now run the command `npm install` in the `/tmp/mcp/do-kubernetes-argocd/` folder.

4.
Verify that the following files or folders exist:

- `/tmp/mcp/do-kubernetes-argocd/`
- `/tmp/mcp/do-kubernetes-argocd/Pulumi.dev.yaml`
- `/tmp/mcp/do-kubernetes-argocd/node_modules`

5.
After this the `github_agent` is done and report back to the `supervisor`

#### Pulumi

1.
Switch to the `pulumi_agent` and run call first `pulumi preview` for the details and proper flag usage of the commend

2.
Then run a `pulumi preview` with the stackname `dirien/do-kubernetes-argocd/dev` and the workdir `/tmp/mcp/do-kubernetes-argocd/`

3.
If there is an error in the `pulumi preview` stop and return

4.
After this the `pulumi_agent` is done and report back to the `supervisor`

#### README

1.
Switch to the `readme_builder_agent` to write and explain `/tmp/mcp/do-kubernetes-argocd/` code and create instructions on how to maintain the code as a user. Create and write all of this into the file `/tmp/mcp/do-kubernetes-argocd/README.md`

2.
Verify that the following files or folders exist:

- `/tmp/mcp/do-kubernetes-argocd/README.md`

3.
Then you are done and report back to the `supervisor`

#### Wrap-up

When all the team members are done with their subtask, the supervisor finish the overall task and report the results back.
