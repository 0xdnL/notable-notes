---
tags: [linux]
title: top
created: '2020-02-24T12:30:59.456Z'
modified: '2024-12-02T12:53:16.005Z'
---

# top

> dynamic real-time view of running processes

[[htop]]

## options

```sh
-e   # enforce-Task-Memory-Scaling    as: -e  k|m|g|t|p     k=kibibytes,m=mebibytes,g=gibibytes,t=tebibytes,p=pebibytes
-E   # enforce-Summary-Memory-Scaling as: -E  k|m|g|t|p|e   k=kibibytes,m=mebibytes,g=gibibytes,t=tebibytes,p=pebibytes,e=exbibytes
-s   # starts top with secure mode forced, even for root
-S   # cumulative-time toggle, starts with the last remembered `S' state reversed

-u,-U [number|name] # display  only  processes  with  a  user id or user name matching that given
                    # prepending `!' to the user id or name instructs top to display only processes with users not matching the one provided
```


## usage

```sh
top   # starts in standard view
```

```sh
⇧ + e, E       # (uppercase) to change the memory scale globally (for all memory values displayed)
               # press mutliple time to cycles through different units (KB, MB, GB, etc.)

# Sorting Mode
⇧ + m, M       # sort by memory
⇧ + p, P       # sort by cpu
⇧ + n, N       # sort by ..
⇧ + t, T       # sort by ..

H             # toggle the view to show or hide threads
V             # Tree/Hierarchical View - showing parent-child relationships, which is particularly useful for understanding the grouping of processes and their origins


u + username    # filter and display processes owned by a particular user
'f' or 'F'      # Fields Management Mode (Fields Select) this mode allows users to choose which columns/fields are displayed in the top output. Users can add or remove fields to customize the view according to their preferences
Z               # Color, Highlight, and Bold Mode**:users can enter a customization mode that allows them to change colors, and highlight or bold certain lines or text, making it easier to distinguish between different types of information.
```

## see also

- [[procps]]
- [[free]]
- [[procfs]]

