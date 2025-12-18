---
tags: [linux, systemd]
title: journalctl
created: '2019-08-19T09:11:28.583Z'
modified: '2025-12-09T13:09:55.626Z'
---

# journalctl

> query systemd journal

[[systemd]], [[systemctl]]

## option

```sh
-f, --follow                    # show only the most recent journal entries, and continuously print new entries as they are appended to the journal
-u, --unit=UNIT|PATTERN         # show messages for the specified systemd unit UNIT (such as a service unit), or for any of the units matched by PATTERN
-k, --dmesg                     # show only kernel messages, implies -b and adds the match "_TRANSPORT=kernel"
-r, --reverse                   # reverse output so that the newest entries are displayed first.

-o, --output=OPT                # controls the formatting of the journal entries that are shown
--output=short                  # default, generates an output that is mostly identical to the formatting of classic syslog files, showing one line per journal entry
--output=short-full             # similar, but shows timestamps in the format the --since= and --until= options accept
--output=short-unix             # similar, but shows seconds passed since January 1st 1970 UTC instead of wallclock timestamps ("UNIX time")
--outpout=verbose               # shows the full-structured entry items with all fields.
--outpout=export                # serializes the journal into a binary (but mostly text-based) stream suitable for backups and network transfer

--outpout=json  # formats entries as JSON objects, separated by newline characters (see Journal JSON Format[2] for more information). Field values are generally encoded as JSON strings, with three exceptions:
                # 1. Fields larger than 4096 bytes are encoded as null values. (This may be turned off by passing --all, but be aware that this may allocate overly long JSON objects.)
                # 2. Journal entries permit non-unique fields within the same log entry. JSON does not allow non-unique fields within objects. Due to this, if a non-unique field is encountered a JSON array is used as field value, listing all field values as elements
                # 3. Fields containing non-printable or non-UTF8 bytes are encoded as arrays containing the raw bytes individually formatted as unsigned numbers
                # Note that this encoding is reversible (with the exception of the size limit)

--outpout=json-pretty # formats JSON data structures, but formats them in multiple lines in order to make them more readable by humans.
--outpout=json-sse    # formats JSON data structures, but wraps them in a format suitable for Server-Sent Events[3].
--outpout=json-seq    # formats JSON data structures, but prefixes them with an ASCII Record Separator character (0x1E) and suffixes them with an ASCII Line Feed character (0x0A), in accordance with JavaScript Object Notation (JSON)
--outpout=cat         # generates a very terse output, only showing the actual message of each journal entry with no metadata, not even a timestamp. If combined with the --output-fields= option will output the listed fields for each log record, instead of the message.
--outpout=with-unit   # similar to short-full, but prefixes the unit and user unit names instead of the traditional syslog identifier. Useful when using templated instances, as it will include the arguments in the unit names.
```

## usage

```sh
journalctl -f                   # follow

journalctl -u ssh               # Show Logs for a systemd ServicePermalink

journalctl -k                   # View Kernel MessagesPermalink

journalctl -o json-pretty       # Change the Log Output FormatPermalink

journalctl --vacuum-size=2G     # Manually Clean Up Archived LogsPermalink


journalctl -xefu SERVICE

journalctl -D /var/log/journal -u k3s
```

## see also

- [[k3s]]
- [[syslog]]
- [Use journalctl to View Your System's Logs](https://www.linode.com/docs/quick-answers/linux/how-to-use-journalctl/)
- [systemd/man/journalctl](https://www.freedesktop.org/software/systemd/man/journalctl#-o)
