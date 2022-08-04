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

Clone the repository:

```bash

  cd /opt
  git clone https://gitlab.com/gcoop-libre/gitlab-bash-utils

```

Add to `$HOME/.bashrc`:

```bash

# command and aliases of gitlab bash utils
if [[ -d "$PWD/gitlab-bash-utils" ]]
then
  PATH="$PWD/gitlab-bash-utils:$PATH"
  source $PWD/gitlab-bash-utils/gl-src-alias
fi

```

## dependencies

The main dependency is `glab`, install from:

   https://github.com/profclems/glab

Other utils tools:

```bash

apt-get install coreutils curl jq gawk moreutils

```

## commands reference

- [gl commands](gl-help.md)

## License

GNU General Public License, GPLv3.

## Author Information

This repo was created in 2022 by
 [Osiris Alejandro Gomez](https://osiux.com/), worker cooperative of
 [gcoop Cooperativa de Software Libre](https://www.gcoop.coop/).
