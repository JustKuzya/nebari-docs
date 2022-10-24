---
title: API Documentation
description: Reference to API docs
---
# API Documentation
## Table of Contents


<a id="qhub.qhub.destroy"></a>

### qhub.qhub.destroy

<a id="qhub.qhub.initialize"></a>

### qhub.qhub.initialize

<a id="qhub.qhub.render"></a>

### qhub.qhub.render

<a id="qhub.qhub.render.render_contents"></a>

#### render\_contents

```python
def render_contents(config: Dict)
```

Dynamically generated contents from QHub configuration

<a id="qhub.qhub.render.gen_gitignore"></a>

#### gen\_gitignore

```python
def gen_gitignore(config)
```

Generate `.gitignore` file.
Add files as needed.

<a id="qhub.qhub.render.gen_cicd"></a>

#### gen\_cicd

```python
def gen_cicd(config)
```

Use cicd schema to generate workflow files based on the
`ci_cd` key in the `config`.

For more detail on schema:
GiHub-Actions - qhub/providers/cicd/github.py
GitLab-CI - qhub/providers/cicd/gitlab.py

<a id="qhub.qhub.render.inspect_files"></a>

#### inspect\_files

```python
def inspect_files(source_dirs: str,
                  output_dirs: str,
                  source_base_dir: str,
                  output_base_dir: str,
                  ignore_filenames: List[str] = None,
                  ignore_directories: List[str] = None,
                  deleted_paths: List[str] = None,
                  contents: Dict[str, str] = None)
```

Return created, updated and untracked files by computing a checksum over the provided directory

**Arguments**:

- `source_dirs` _str_ - The source dir used as base for comparssion
- `output_dirs` _str_ - The destination dir which will be matched with
- `source_base_dir` _str_ - Relative base path to source directory
- `output_base_dir` _str_ - Relative base path to output directory
- `ignore_filenames` _list[str]_ - Filenames to ignore while comparing for changes
- `ignore_directories` _list[str]_ - Directories to ignore while comparing for changes
- `deleted_paths` _list[str]_ - Paths that if exist in output directory should be deleted
- `contents` _dict_ - filename to content mapping for dynamically generated files

<a id="qhub.qhub.render.hash_file"></a>

#### hash\_file

```python
def hash_file(file_path: str)
```

Get the hex digest of the given file

**Arguments**:

- `file_path` _str_ - path to file

<a id="qhub.qhub.render.set_env_vars_in_config"></a>

#### set\_env\_vars\_in\_config

```python
def set_env_vars_in_config(config)
```

For values in the config starting with 'QHUB_SECRET_XXX' the environment
variables are searched for the pattern XXX and the config value is
modified. This enables setting secret values that should not be directly
stored in the config file.

NOTE: variables are most likely written to a file somewhere upon render. In
order to further reduce risk of exposure of any of these variables you might
consider preventing storage of the terraform render output.

<a id="qhub.qhub.cli.support"></a>

### qhub.qhub.cli.support

<a id="qhub.qhub.cli.deploy"></a>

### qhub.qhub.cli.deploy

<a id="qhub.qhub.cli._init"></a>

### qhub.qhub.cli.\_init

<a id="qhub.qhub.cli._init.handle_init"></a>

#### handle\_init

```python
def handle_init(inputs: InitInputs)
```

Take the inputs from the `nebari init` command, render the config and write it to a local yaml file.

<a id="qhub.qhub.cli._init.check_cloud_provider_creds"></a>

#### check\_cloud\_provider\_creds

```python
def check_cloud_provider_creds(ctx: typer.Context, cloud_provider: str)
```

Validate that the necessary cloud credentials have been set as environment variables.

<a id="qhub.qhub.cli._init.check_auth_provider_creds"></a>

#### check\_auth\_provider\_creds

```python
def check_auth_provider_creds(ctx: typer.Context, auth_provider: str)
```

Validating the the necessary auth provider credentials have been set as environment variables.

<a id="qhub.qhub.cli._init.check_project_name"></a>

#### check\_project\_name

```python
def check_project_name(ctx: typer.Context, project_name: str)
```

Validate the project_name is acceptable. Depends on `cloud_provider`.

<a id="qhub.qhub.cli._init.guided_init_wizard"></a>

#### guided\_init\_wizard

```python
def guided_init_wizard(ctx: typer.Context, guided_init: str)
```

Guided Init Wizard is a user-friendly questionnaire used to help generate the `nebari-config.yaml`.

<a id="qhub.qhub.cli.destroy"></a>

### qhub.qhub.cli.destroy

<a id="qhub.qhub.cli.initialize"></a>

### qhub.qhub.cli.initialize

<a id="qhub.qhub.cli.render"></a>

### qhub.qhub.cli.render

<a id="qhub.qhub.cli"></a>

### qhub.qhub.cli

<a id="qhub.qhub.cli.upgrade"></a>

### qhub.qhub.cli.upgrade

<a id="qhub.qhub.cli.validate"></a>

### qhub.qhub.cli.validate

<a id="qhub.qhub.cli._keycloak"></a>

### qhub.qhub.cli.\_keycloak

<a id="qhub.qhub.cli._keycloak.add_user"></a>

#### add\_user

```python
@app_keycloak.command(name="adduser")
def add_user(add_users: Tuple[str, str] = typer.Option(
    ..., "--user", help="Provide both: <username> <password>"),
             config_filename: str = typer.Option(
                 ...,
                 "-c",
                 "--config",
                 help="qhub configuration file path",
             ))
```

Add a user to Keycloak. User will be automatically added to the [italic]analyst[/italic] group.

<a id="qhub.qhub.cli._keycloak.list_users"></a>

#### list\_users

```python
@app_keycloak.command(name="listusers")
def list_users(config_filename: str = typer.Option(
    ...,
    "-c",
    "--config",
    help="qhub configuration file path",
))
```

List the users in Keycloak.

<a id="qhub.qhub.cli.keycloak"></a>

### qhub.qhub.cli.keycloak

<a id="qhub.qhub.cli.cost"></a>

### qhub.qhub.cli.cost

<a id="qhub.qhub.cli.main"></a>

### qhub.qhub.cli.main

<a id="qhub.qhub.cli.main.OrderCommands"></a>

## OrderCommands Objects

```python
class OrderCommands(TyperGroup)
```

<a id="qhub.qhub.cli.main.OrderCommands.list_commands"></a>

#### list\_commands

```python
def list_commands(ctx: Context)
```

Return list of commands in the order appear.

<a id="qhub.qhub.cli.main.init"></a>

#### init

```python
@app.command()
def init(cloud_provider: str = typer.Argument(
    "local",
    help=f"options: {enum_to_list(ProviderEnum)}",
    callback=check_cloud_provider_creds,
    is_eager=True,
),
         guided_init: bool = typer.Option(
             False,
             help=GUIDED_INIT_MSG,
             callback=guided_init_wizard,
             is_eager=True,
         ),
         project_name: str = typer.Option(
             ...,
             "--project-name",
             "--project",
             "-p",
             callback=check_project_name,
         ),
         domain_name: str = typer.Option(
             ...,
             "--domain-name",
             "--domain",
             "-d",
         ),
         namespace: str = typer.Option("dev", ),
         auth_provider: str = typer.Option(
             "password",
             help=f"options: {enum_to_list(AuthenticationEnum)}",
             callback=check_auth_provider_creds,
         ),
         auth_auto_provision: bool = typer.Option(False, ),
         repository: str = typer.Option(None, ),
         repository_auto_provision: bool = typer.Option(False, ),
         ci_provider: str = typer.Option(
             None,
             help=f"options: {enum_to_list(CiEnum)}",
         ),
         terraform_state: str = typer.Option(
             "remote", help=f"options: {enum_to_list(TerraformStateEnum)}"),
         kubernetes_version: str = typer.Option("latest", ),
         ssl_cert_email: str = typer.Option(None, ),
         disable_prompt: bool = typer.Option(
             False,
             is_eager=True,
         ))
```

Create and initialize your [purple]nebari-config.yaml[/purple] file.

This command will create and initialize your [purple]nebari-config.yaml[/purple] :sparkles:

This file contains all your Nebari cluster configuration details and,
is used as input to later commands such as [green]nebari render[/green], [green]nebari deploy[/green], etc.

If you're new to Nebari, we recommend you use the Guided Init wizard.
To get started simply run:

        [green]nebari init --guided-init[/green]

<a id="qhub.qhub.cli.main.validate"></a>

#### validate

```python
@app.command(rich_help_panel=SECOND_COMMAND_GROUP_NAME)
def validate(config: str = typer.Option(
    ...,
    "--config",
    "-c",
    help=
    "qhub configuration yaml file path, please pass in as -c/--config flag",
),
             enable_commenting: bool = typer.Option(
                 False,
                 "--enable_commenting",
                 help="Toggle PR commenting on GitHub Actions"))
```

Validate the values in the [purple]nebari-config.yaml[/purple] file are acceptable.

<a id="qhub.qhub.cli.main.render"></a>

#### render

```python
@app.command(rich_help_panel=SECOND_COMMAND_GROUP_NAME)
def render(
        output: str = typer.Option(
            "./",
            "-o",
            "--output",
            help="output directory",
        ),
        config: str = typer.Option(
            ...,
            "-c",
            "--config",
            help="nebari configuration yaml file path",
        ),
        dry_run: bool = typer.
    Option(
        False,
        "--dry-run",
        help=
        "simulate rendering files without actually writing or updating any files",
    ))
```

Dynamically render the Terraform scripts and other files from your [purple]nebari-config.yaml[/purple] file.

<a id="qhub.qhub.cli.main.deploy"></a>

#### deploy

```python
@app.command()
def deploy(
        config: str = typer.Option(
            ...,
            "--config",
            "-c",
            help="nebari configuration yaml file path",
        ),
        output: str = typer.Option(
            "./",
            "-o",
            "--output",
            help="output directory",
        ),
        dns_provider: str = typer.Option(
            False,
            "--dns-provider",
            help="dns provider to use for registering domain name mapping",
        ),
        dns_auto_provision: bool = typer.
    Option(
        False,
        "--dns-auto-provision",
        help=
        "Attempt to automatically provision DNS. For Auth0 is requires environment variables AUTH0_DOMAIN, AUTH0_CLIENTID, AUTH0_CLIENT_SECRET",
    ),
        disable_prompt: bool = typer.Option(
            False,
            "--disable-prompt",
            help="Disable human intervention",
        ),
        disable_render: bool = typer.Option(
            False,
            "--disable-render",
            help="Disable auto-rendering in deploy stage",
        ))
```

Deploy the Nebari cluster from your [purple]nebari-config.yaml[/purple] file.

<a id="qhub.qhub.cli.main.destroy"></a>

#### destroy

```python
@app.command()
def destroy(
        config: str = typer.Option(...,
                                   "-c",
                                   "--config",
                                   help="qhub configuration file path"),
        output: str = typer.Option(
            "./"
            "-o",
            "--output",
            help="output directory",
        ),
        disable_render: bool = typer.Option(
            False,
            "--disable-render",
            help="Disable auto-rendering before destroy",
        ),
        disable_prompt: bool = typer.
    Option(
        False,
        "--disable-prompt",
        help=
        "Destroy entire Nebari cluster without confirmation request. Suggested for CI use.",
    ))
```

Destroy the Nebari cluster from your [purple]nebari-config.yaml[/purple] file.

<a id="qhub.qhub.cli.main.cost"></a>

#### cost

```python
@app.command(rich_help_panel=SECOND_COMMAND_GROUP_NAME)
def cost(path: str = typer.Option(
    None,
    "-p",
    "--path",
    help=
    "Pass the path of your stages directory generated after rendering QHub configurations before deployment",
),
         dashboard: bool = typer.Option(
             True,
             "-d",
             "--dashboard",
             help="Enable the cost dashboard",
         ),
         file: str = typer.Option(
             None,
             "-f",
             "--file",
             help="Specify the path of the file to store the cost report",
         ),
         currency: str = typer.Option(
             "USD",
             "-c",
             "--currency",
             help="Specify the currency code to use in the cost report",
         ),
         compare: bool = typer.Option(
             False,
             "-cc",
             "--compare",
             help="Compare the cost report to a previously generated report",
         ))
```

Estimate the cost of deploying Nebari based on your [purple]nebari-config.yaml[/purple]. [italic]Experimental.[/italic]

[italic]This is still only experimental using Infracost under the hood.
The estimated value is a base cost and does not include usage costs.[/italic]

<a id="qhub.qhub.cli.main.upgrade"></a>

#### upgrade

```python
@app.command(rich_help_panel=SECOND_COMMAND_GROUP_NAME)
def upgrade(
        config: str = typer.Option(
            ...,
            "-c",
            "--config",
            help="qhub configuration file path",
        ),
        attempt_fixes: bool = typer.
    Option(
        False,
        "--attempt-fixes",
        help=
        "Attempt to fix the config for any incompatibilities between your old and new QHub versions.",
    ))
```

Upgrade your [purple]nebari-config.yaml[/purple] from pre-0.4.0 to 0.4.0.

Due to several breaking changes that came with the 0.4.0 release, this utility is available to help
update your [purple]nebari-config.yaml[/purple] to comply with the introduced changes.
See the project [green]RELEASE.md[/green] for details.

<a id="qhub.qhub.cli.main.support"></a>

#### support

```python
@app.command(rich_help_panel=SECOND_COMMAND_GROUP_NAME)
def support(config_filename: str = typer.Option(
    ...,
    "-c",
    "--config",
    help="qhub configuration file path",
),
            output: str = typer.Option(
                "./qhub-support-logs.zip",
                "-o",
                "--output",
                help="output filename",
            ))
```

Support tool to write all Kubernetes logs locally and compress them into a zip file.

The Nebari team recommends k9s to manage and inspect the state of the cluster.
However, this command occasionally helpful for debugging purposes should the logs need to be shared.

