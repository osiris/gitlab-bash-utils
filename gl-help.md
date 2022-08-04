---
fontsize: 8pt
code-block-font-size: 8pt
classoption: landscape
---

# `gl prj` commands


## `gl-prj-config` Apply project settings defined in `~/.gl-config`

### Usage

```bash

  gl-prj-config GL_PROJECT_ID

```

### Defaults

| variable                                                     | value |
|--------------------------------------------------------------|-------|
| GL_PROJECT_ONLY_ALLOW_MERGE_IF_PIPELINE_SUCCEEDS             | true  |
| GL_PROJECT_MERGE_REQUESTS_ENABLED                            | true  |
| GL_PROJECT_ALLOW_MERGE_ON_SKIPPED_PIPELINE                   | false |
| GL_PROJECT_ONLY_ALLOW_MERGE_IF_ALL_DISCUSSIONS_ARE_RESOLVED  | true  |

### Example

```bash

  gl-prj-config 34078674

  {
    "only_allow_merge_if_pipeline_succeeds": true,
    "merge_requests_enabled": true,
    "allow_merge_on_skipped_pipeline": false,
    "only_allow_merge_if_all_discussions_are_resolved": true
  }

```


## `gl-prj-list` List all _projects_ in _GitLab_ for current user

### Usage

```bash

  gl-prj-list

```

### Example

```bash

  gl-prj-list | grep osiux | grep bash

	37091293 osiux/gilabash git@gitlab.com:osiux/gilabash.git fun scripts in bash
	6663951 osiux/git-bash-utils git@gitlab.com:osiux/git-bash-utils.git Repository of bash scripts for various git utils.
	34554594 osiux/gitlab-bash-utils git@gitlab.com:osiux/gitlab-bash-utils.git Useful bash scripts for various gitlab utils.
	21388424 osiux/links-bash-utils git@gitlab.com:osiux/links-bash-utils.git organize bookmarks from links.txt and convert to links.org
	22673434 osiux/log-bash-utils git@gitlab.com:osiux/log-bash-utils.git useful scripts for logs files
	6663957 osiux/media-bash-utils git@gitlab.com:osiux/media-bash-utils.git organize photos and videos using metadata
	6663960 osiux/minimal-bash-prompt git@gitlab.com:osiux/minimal-bash-prompt.git A minimal prompt for bash
	6663969 osiux/org-bash-utils git@gitlab.com:osiux/org-bash-utils.git utils bash scripts for org-mode
	22624065 osiux/redmine-bash-utils git@gitlab.com:osiux/redmine-bash-utils.git Bash scripts for using Redmine from TTY
	6664008 osiux/txt-bash-jrnl git@gitlab.com:osiux/txt-bash-jrnl.git A simple command line journal application that stores your journal in a plain text file, developed in bash and inspired in http://jrnl.sh

```


## `gl-prj-upload` Upload file in project and return _URL_ link in _Markdown_

### Usage

```bash

  gl-prj-upload FILE

```

### Example

```bash

  PROJECT_ID=34078674 gl-prj-upload 2022-08-04-003117.png

  ![2022-08-04-003117](/uploads/74cfea3e7792c30efd9c794deb91ca8f/2022-08-04-003117.png)

```


# `gl src` commands


## `gl-src-check` Check syntax using shellcheck and group errors by code

### Usage

```bash

  gl-src-check

```

### Example

```bash

  gl-src-check

  gl-src-check                                  SC2034
  gl-mr-link                                    SC2034
  gl-mr-new                                     SC1003
  gl-prj-config                                 SC1090 SC2086
  gl-prj-upload                                 SC1090 SC2162

```


## `gl-src-help` Generate Markdown Help

### Usage

```bash

  gl-src-help

```

### Description

Generate a markdown output for usage of each command script.


## `gl-src-table` Generate Markdown Table Overview

### Usage

```bash

  gl-src-table

```

### Description

Generate a markdown table output for each command script.

