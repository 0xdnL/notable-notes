---
tags: [coreutils]
title: date
created: '2019-07-30T06:19:49.033Z'
modified: '2023-11-11T16:04:18.105Z'
---

# date

> print or set the system date and time

## install

```sh
brew install coreutils      # uses gnu-date
```

## option

```sh
-d,       --date=STRING         # display time described by STRING, not 'now'
          --debug               # annotate the parsed date, and warn about questionable usage to stderr
-f,       --file=DATEFILE       # like --date; once for each line of DATEFILE
-I[FMT],  --iso-8601[=FMT]      # output date/time in ISO 8601 format. FMT='date' for date only (the default), 'hours', 'minutes', 'seconds', or 'ns' for date and time to the indicated precision. Example: 2006-08-14T02:34:56-06:00
          --resolution          # output the available resolution of timestamps Example: 0.000000001
-R,       --rfc-email           # output date and time in RFC 5322 format. Example: Mon, 14 Aug 2006 02:34:56 -0600
          --rfc-3339=FMT        # output date/time in RFC 3339 format. FMT='date', 'seconds', or 'ns' for date and time to the indicated precision. Example: 2006-08-14 02:34:56-06:00
-r,       --reference=FILE      # display the last modification time of FILE
-s,       --set=STRING          # set time described by STRING
-u,       --utc, --universal    # print or set Coordinated Universal Time (UTC)
          --help                # display this help and exit
          --version             # output version information and exit
```

## string format

```sh
man strftime    # get formats

%F          # is equivalent to "%Y-%m-%d"
%R          # is equivalent to "%H:%M"
%s          # unix timestamp

date --help   # gnu-date format info
%%    # a literal %
%a    # locale's abbreviated weekday name (e.g., Sun)
%A    # locale's full weekday name (e.g., Sunday)
%b    # locale's abbreviated month name (e.g., Jan)
%B    # locale's full month name (e.g., January)
%c    # locale's date and time (e.g., Thu Mar  3 23:05:25 2005)
%C    # century; like %Y, except omit last two digits (e.g., 20)
%d    # day of month (e.g., 01)
%D    # date; same as %m/%d/%y
%e    # day of month, space padded; same as %_d
%F    # full date; like %+4Y-%m-%d
%g    # last two digits of year of ISO week number (see %G)
%G    # year of ISO week number (see %V); normally useful only with %V
%h    # same as %b
%H    # hour (00..23)
%I    # hour (01..12)
%j    # day of year (001..366)
%k    # hour, space padded ( 0..23); same as %_H
%l    # hour, space padded ( 1..12); same as %_I
%m    # month (01..12)
%M    # minute (00..59)
%n    # a newline
%N    # nanoseconds (000000000..999999999)
%p    # locale's equivalent of either AM or PM; blank if not known
%P    # like %p, but lower case
%q    # quarter of year (1..4)
%r    # locale's 12-hour clock time (e.g., 11:11:04 PM)
%R    # 24-hour hour and minute; same as %H:%M
%s    # seconds since the Epoch (1970-01-01 00:00 UTC)
%S    # second (00..60)
%t    # a tab
%T    # time; same as %H:%M:%S
%u    # day of week (1..7); 1 is Monday
%U    # week number of year, with Sunday as first day of week (00..53)
%V    # ISO week number, with Monday as first day of week (01..53)
%w    # day of week (0..6); 0 is Sunday
%W    # week number of year, with Monday as first day of week (00..53)
%x    # locale's date representation (e.g., 12/31/99)
%X    # locale's time representation (e.g., 23:13:48)
%y    # last two digits of year (00..99)
%Y    # year
%z    # +hhmm numeric time zone (e.g., -0400)
%:z   # +hh:mm numeric time zone (e.g., -04:00)
%::z  # +hh:mm:ss numeric time zone (e.g., -04:00:00)
%:::z # numeric time zone with : to necessary precision (e.g., -04, +05:30)
%Z    # alphabetic time zone abbreviation (e.g., EDT)
```

## usage

```sh
date "+%s"                        # get unix timestamp
date "+%F_%T"                     # 2020-01-30_13:16:52
date "+%F_%H-%M"                  # 2020-01-30_13-16
date +"%m-%d-%y_%H-%M"            # month day year, hour minute

date -d "2023-11-12T03:47:43+00:00" "+%Y-%m-%dT%H:%M:%S%z"

date -r "1563533492792"           # convert unix timestamp on bsd/macos
gdate -d "@1563533492792"         # convert unix timestamp on linux

date -u -d "$(date -d "8am")"     # convert local time to UTC

date -d "$(date -u -d "10am")"    # convert UTC time to local

date -v -11d                      # subtract 11 days from current date on bsd/macos

gdate -I -d "2019-01-01 + 1 day"          # add 1 day to date
gdate -d "$(gdate +%F) + 1 day" +%F       # add 1 day
for i in {1..5}; do mkdir $(gdate -d "$(gdate +%F) + $i day" +%F_%a); done

gdate -d "2019-01-01" +%A                 # get short weekday from date

# calculate days difference
echo "$(( (  $(gdate "+%s") - $(gdate -d "2020-10-13T08:30:10+00:00" "+%s") )/(60*60*24) ))" 
```

## see also

- [[coreutils]]
- [[cal]]
- [[strftime]]
- [[hwclock]]
- [[timedatectl]]
