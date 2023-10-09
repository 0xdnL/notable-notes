---
title: glab
created: '2023-09-13T11:14:09.200Z'
modified: '2023-09-13T11:22:20.257Z'
---

# glab

## install

```sh
brew install glab
```

## env

```sh
GITLAB_TOKEN                      # auth token for API requests
GITLAB_HOST, GL_HOST              # specify GitLab server if self-managed
GIT_REMOTE_URL_VAR, REMOTE_ALIAS  # 'git remote' variable or alias that contains the GitLab URL
VISUAL, EDITOR                    # editor tool to use for authoring text
BROWSER                           # web browser to use for opening links
GLAMOUR_STYLE                     # environment variable to set your desired Markdown renderer style opts: ark, light, notty
NO_PROMPT                         # set to 1 (true) or 0 (false) to disable or enable prompts
NO_COLOR                          # set to any value to avoid printing ANSI escape sequences for color output
FORCE_HYPERLINKS                  # set to 1 to force hyperlinks in output, even when not outputting to a TTY
GLAB_CONFIG_DIR                   # set to a directory path to override the global configuration location
```

## usage

```sh
glab auth login --hostname HOST     # selfhosted gitlab

glab auth status

glab repo list --all

glab config set editor vim
glab config set token xxxxxx
glab config set remote_alias origin
glab config set browser mybrowser
```

## see also

- [[gh]]
- [gitlab.com/gitlab-org/cli](https://gitlab.com/gitlab-org/cli)
