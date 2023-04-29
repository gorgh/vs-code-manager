# Visual Studio Code manager

Visual Studio Code install and update management for UNIX users with limited administrator privileges.
> Administrator privileges may be limited by your company for security reasons.

## Install

Add this repository to your `PATH` environment variable:

```sh
cat << EOF >> "$HOME/.bashrc" 
export PATH="<repository direname>:\${PATH}"
EOF
```

Then, execute the `install-code` command to automatically install Visual Studio Code.
> The last Visual Studio Code tarball will be downloaded in the `archives` directory and extracted in the `install` directory.
> The last installation directory is identified with the `install/latest` symlink.

A XDG Desktop Entry is also installed in your local environment by the `install-code` command.

## Update

When Visual Studio Code warns you that a new version is available:

* Close all your Visual Studio Code sessions (with `ctrl+Q`).
* Execute the `install-code` command to automatically update your Visual Studio Code installation.
* Restart Visual Studio Code (see [start Visual Studio Code](#start)).

## Start

### Through the CLI

Execute the `code` command to start Visual Studio Code.

### Through the XDG Desktop Entry

You can also use the XDG Desktop Entry installed in your local environment by the `install-code` command.

### Security concerns

As Visual Studio Code is not install as a system package, it will be executed **outside the sandbox environment**.

## Manage proxy settings

As your company is limiting your administrator privileges, it may also impose you to access the internet through a proxy.

To allow Visual Studio Code to access the internet, you can modify the `proxy` file to export the proxy configuration variables:

```sh
proxy_address='http://[<user>[:<password>]@]<url>:<port>'
export http_proxy="${proxy_address}"
export https_proxy="${proxy_address}"
export no_proxy='localhost,127.0.0.1,<intranet domain>'
export HTTP_PROXY="${http_proxy}"
export HTTPS_PROXY="${https_proxy}"
export NO_PROXY="${no_proxy}"
```

This file will be automatically sourced by the `code` and `install-code` commands.
