# _GitLab Bash Utils_

## Tools Overview

Repository of useful scripts for _GitLab_.

| script                  | alias  | description                                                            |
|-------------------------|--------|------------------------------------------------------------------------|
| `gl-ci-lint           ` | `glcl` | Validate `.gitlab-ci.yml`                                              |
| `gl-config            ` | `    ` | Overwrite `~/.gl-config` with default config values                    |
| `gl-issue-check       ` | `glic` | Get issue URL link in Markdown format with checkbox                    |
| `gl-issue-jrnl        ` | `glij` | Get Issue group and project _ID_ with title for `jrnl`                 |
| `gl-issue-link        ` | `glik` | Get the issue title with the _URL_ link in _Markdown_ format           |
| `gl-issue-list        ` | `glil` | Get the issue title with _URL_ link in _Markdown_ as a list item       |
| `gl-issue-new         ` | `gliw` | Create issue with defaults defined in `~/.gl-config`                   |
| `gl-issue-note        ` | `glin` | Insert note in _Issue_ converting hh:mm time format into `/spend` time |
| `gl-issue-spend       ` | `glis` | Insert `/spend` time in _Issue_ converting from `hh:mm` time format    |
| `gl-issue-title       ` | `glit` | Get title of Issue                                                     |
| `gl-issue-url         ` | `gliu` | Get _URL_ of Issue                                                     |
| `gl-mr-check          ` | `glmc` | Get _MR_ _URL_ link in _Markdown_ format with checkbox                 |
| `gl-mr-jrnl           ` | `glmj` | Get _MR_ group and project _ID_ with title for `jrnl`                  |
| `gl-mr-link           ` | `glmk` | Get the _MR_ title with the _URL_ link in _Markdown_ format            |
| `gl-mr-new            ` | `glmw` | Create _MR_ with default values defined in `~/.gl-config`              |
| `gl-mr-note           ` | `glmn` | Insert note in _MR_ converting `hh:mm` time format into `/spend` time  |
| `gl-mr-spend          ` | `glms` | Insert `/spend` time in _MR_ converting from `hh:mm` time format       |
| `gl-mr-title          ` | `glmt` | Get title of _MR_                                                      |
| `gl-mr-url            ` | `glmu` | Get _URL_ of _MR_                                                      |
| `gl-notifications-get ` | `glnu` | Get _User_ notification level defined in _GitLab_                      |
| `gl-prj-config        ` | `    ` | Apply project settings defined in `~/.gl-config`                       |
| `gl-prj-list          ` | `glpl` | List all _projects_ in _GitLab_ for current user                       |
| `gl-prj-upload        ` | `    ` | Upload file in project and return _URL_ link in _Markdown_             |
| `gl-src-check         ` | `glsk` | Check syntax using shellcheck and group errors by code                 |
| `gl-src-common        ` | `    ` | Common variables and functions                                         |
| `gl-src-help          ` | `glsh` | Generate Markdown Help                                                 |
| `gl-src-table         ` | `glst` | Generate Markdown Table Overview                                       |

## Install

### Manual

Clone the repository, for example in `/opt` directory:

```bash

  cd /opt
  git clone https://gitlab.com/gcoop-libre/gitlab-bash-utils

```

Add to `$HOME/.bashrc`:

```bash

# command and aliases of gitlab bash utils
if [[ -d "/opt/gitlab-bash-utils" ]]
then
  PATH="/opt/gitlab-bash-utils:$PATH"
  source /opt/gitlab-bash-utils/gl-src-alias
fi

```

## dependencies

The main dependency is `glab`, install from:

   https://github.com/profclems/glab

Other utils tools:

```bash

apt-get install coreutils curl jq gawk moreutils

```

## Configuration

### `glab` config

Ensure configure `glab` in `~/.config/glab-cli/config.yml`, for example:

```yaml
git_protocol: https
editor:
browser:
glamour_style: dark
check_update: false
hosts:
    gitlab.com:
        token: z4r4z4acddfafafa
        api_host: gitlab.com
        git_protocol: https
        api_protocol: https
        user: osiux
    git.example.com:
        api_host: git.example.com
        token: z4r4z4acddfafafa
        git_protocol: https
        api_protocol: https
        skip_tls_verify: "false"
        user: osiris
```

Remember replace _hostnames_, _usernames_ and _tokens_.

### `glab` aliases

You can define custom aliases in `~/.config/glab-cli/aliases.yml`, for
example:

```yaml
ci: pipeline ci
co: mr checkout
ic: issue close
il: issue list
in: issue note
iu: issue update
iv: issue view
iw: issue new
ma: mr approve
mc: mr close
ml: mr list
mv: mr view
my: mr ready
```

### `gl`

Ensure configure `gl` in `~/.gl-config`, for example:

```ini
GL_ACCESS_ADMIN: 60
GL_ACCESS_DEVELOPER: 30
GL_ACCESS_GUEST: 10
GL_ACCESS_MAINTAINER: 40
GL_ACCESS_MINIMAL: 5
GL_ACCESS_NONE: 0
GL_ACCESS_OWNER: 50
GL_ACCESS_REPORTER: 20
GL_BRANCH: master
GL_GITLAB_COM_DEFAULT_ASSIGNEE: osiux
GL_GITLAB_COM_PROXY_HTTP_ENABLED: 0
GL_GIT_EXAMPLE_COM_DEFAULT_ASSIGNEE: osiris
GL_GIT_EXAMPLE_COM_PROXY_HTTP_ENABLED: 1
GL_GIT_EXAMPLE_COM_PROXY_HTTP_HOST: 127.0.0.1
GL_GIT_EXAMPLE_COM_PROXY_HTTP_PORT: 3128
GL_INFO: 0
GL_MERGE_LEVEL: 40
GL_PROJECT_ALLOW_MERGE_ON_SKIPPED_PIPELINE: false
GL_PROJECT_MERGE_REQUESTS_ENABLED: true
GL_PROJECT_ONLY_ALLOW_MERGE_IF_ALL_DISCUSSIONS_ARE_RESOLVED: true
GL_PROJECT_ONLY_ALLOW_MERGE_IF_PIPELINE_SUCCEEDS: true
GL_PROXY_SOCKS_ENABLED: 1
GL_PROXY_SOCKS_HOST: 127.0.0.1
GL_PROXY_SOCKS_PORT: 90903
GL_PUSH_LEVEL: 40
GL_UNPROTECT_LEVEL: 40
```

### Configure _SSH_ LocalForward to RemoteProxy

If you use a _bastion_ _host_ to access to remote _GitLab_ in private
network, you can define a LocalForward, for example:

```sshconfig

Host bastion
     Hostname 192.168.0.1
     LocalForward  3128  10.0.0.1:3128
     DynamicForward :9090
```

Execute `ssh -fqNC bastion` and you can acces to `git.example.com` trought _Proxy_

Test your _proxy_

```bash
curl -I http://127.0.0.1:3128
```

### Repositories

The access to _GitLab API_ need _HTTP_ remote origin in `~/.git/config`

Replace _SSH_ _URL_:

```gitconfig
[remote "origin"]
	fetch = +refs/heads/*:refs/remotes/origin/*
  url = git@gitlab.com:/osiux/gitlab-bash-utils
```

with _HTTPS_ _URL_:

```gitconfig
[remote "origin"]
	fetch = +refs/heads/*:refs/remotes/origin/*
	url = https://gitlab.com/osiux/gitlab-bash-utils
```

## commands reference

- [gl commands](gl-help.md)

## License

GNU General Public License, GPLv3.

## Author Information

This repo was created in 2022 by
 [Osiris Alejandro Gomez](https://osiux.com/), worker cooperative of
 [gcoop Cooperativa de Software Libre](https://www.gcoop.coop/).
