---
tags: [linux, macos]
title: numfmt
created: '2021-10-19T11:54:38.435Z'
modified: '2024-07-08T11:20:02.887Z'
---

# numfmt

> convert numbers from/to human-readable strings

## install

```sh
brew install coreutils
```

## option

```sh
-d, --delimiter=DELIM     # use DELIM instead of whitespace for field delimiter
    --field=FIELDS        # replace the numbers in these input fields (default=1); see FIELDS below
    --format=FORMAT       # use printf style floating-point FORMAT; see FORMAT below for details
    --from=UNIT           # auto-scale input numbers to UNITs; default is 'none'; see UNIT below
    --from-unit=N         # specify the input unit size (instead of the default 1)
    --grouping            # use locale-defined grouping of digits, e.g. 1,000,000 (which means it has no effect in the C/POSIX locale)
    --header[=N]          # print (without converting) the first N header lines; N defaults to 1 if not specified
    --invalid=MODE        # failure mode for invalid numbers: MODE can be: abort (default), fail, warn, ignore
    --padding=N           # pad the output to N characters; positive N will right-align; negative N will left-align; 
                          #  padding is ignored if the output is wider than N; the default is to automatically pad if a whitespace is found
    --round=METHOD        # use METHOD for rounding when scaling; METHOD can be: up, down, from-zero (default), towards-zero, nearest
    --suffix=SUFFIX       # add SUFFIX to output numbers, and accept optional SUFFIX in input numbers
    --to=UNIT             # auto-scale output numbers to UNITs; see UNIT below
    --to-unit=N           # the output unit size (instead of the default 1)
-z, --zero-terminated     # line delimiter is NUL, not newline

    --debug               # print warnings about invalid input
    --help                # display help and exit
    --version             # output version information and exit
```

### units

```sh
none    # no auto-scaling is done; suffixes will trigger an error

auto    # accept optional single/two letter suffix:
        # 1K = 1000, 1Ki = 1024, 1M = 1000000, 1Mi = 1048576,

si      # auto-scale numbers according to the International System of Units (SI) standard
        # accept optional single letter suffix:
        # 1K = 1000, 1M = 1000000, ...
        # ‘K’  =>  1000^1 = 10^3 (Kilo) (uppercase accepted on input)
        # ‘k’  =>  1000^1 = 10^3 (Kilo) (lowercase used on output)
        # ‘M’  =>  1000^2 = 10^6 (Mega)
        # ‘G’  =>  1000^3 = 10^9 (Giga)
        # ‘T’  =>  1000^4 = 10^{12} (Tera)
        # ‘P’  =>  1000^5 = 10^{15} (Peta)
        # ‘E’  =>  1000^6 = 10^{18} (Exa)
        # ‘Z’  =>  1000^7 = 10^{21} (Zetta)
        # ‘Y’  =>  1000^8 = 10^{24} (Yotta)
        # ‘R’  =>  1000^9 = 10^{27} (Ronna)
        # ‘Q’  =>  1000^{10} = 10^{30} (Quetta)

iec     # auto-scale numbers according to the International Electrotechnical Commission (IEC) standard
        # accept optional single letter suffix:
        # 1K = 1024, 1M = 1048576, ...
        # ‘K’  =>  1024^1 = 2^{10} (Kibi) (uppercase used on output)
        # ‘k’  =>  1024^1 = 2^{10} (Kibi) (lowercase accepted on input)
        # ‘M’  =>  1024^2 = 2^{20} (Mebi)
        # ‘G’  =>  1024^3 = 2^{30} (Gibi)
        # ‘T’  =>  1024^4 = 2^{40} (Tebi)
        # ‘P’  =>  1024^5 = 2^{50} (Pebi)
        # ‘E’  =>  1024^6 = 2^{60} (Exbi)
        # ‘Z’  =>  1024^7 = 2^{70} (Zebi)
        # ‘Y’  =>  1024^8 = 2^{80} (Yobi)
        # ‘R’  =>  1024^9 = 2^{90} (Robi)
        # ‘Q’  =>  1024^{10} = 2^{100} (Quebi)


iec-i   # auto-scale numbers according to the International Electrotechnical Commission (IEC) standard
        # accept optional two-letter suffix:
        # 1Ki = 1024, 1Mi = 1048576, ...
        # ‘Ki’  =>  1024^1 = 2^{10} (Kibi) (uppercase used on output)
        # ‘ki’  =>  1024^1 = 2^{10} (Kibi) (lowercase accepted on input)
        # ‘Mi’  =>  1024^2 = 2^{20} (Mebi)
        # ‘Gi’  =>  1024^3 = 2^{30} (Gibi)
        # ‘Ti’  =>  1024^4 = 2^{40} (Tebi)
        # ‘Pi’  =>  1024^5 = 2^{50} (Pebi)
        # ‘Ei’  =>  1024^6 = 2^{60} (Exbi)
        # ‘Zi’  =>  1024^7 = 2^{70} (Zebi)
        # ‘Yi’  =>  1024^8 = 2^{80} (Yobi)
        # ‘Ri’  =>  1024^9 = 2^{90} (Robi)
        # ‘Qi’  =>  1024^{10} = 2^{100} (Quebi)
```

### usage

```sh
numfmt --to=si 1000               # "1.0K"

numfmt --to=iec 2048              # "2.0K"

numfmt --to=iec-i 4096            # "4.0Ki"

echo "1K" | numfmt --from=si      # "1000"

echo "1K" | numfmt --from=iec     # "1024"

echo "7931556Ki" | numfmt --from=iec-i --to=iec

df -B1 | numfmt --header --field 2-4 --to=si
ls -l  | numfmt --header --field 5   --to=iec
ls -lh | numfmt --header --field 5 --from=iec --padding=10
ls -lh | numfmt --header --field 5 --from=iec --format "%10f"


numfmt --field=2 --from-unit=1024 --to=iec-i --suffix B < /proc/meminfo  | sed 's/ kB//' | head -n4
numfmt --field=2 --from-unit=1024 --to=iec-i --suffix B < <(echo 'MemTotal:       263761228 kB')  |   sed 's/ kB//'
```

## see also

- [[coreutils]]
- [[free]]
- [[dd]], [[du]], [[df]]
- [[crane]], [[kubectl]]
- [gnu.org/coreutils/manual/numfmt](https://www.gnu.org/software/coreutils/manual/html_node/numfmt-invocation.html)
- [pixelbeat.org/docs/numfmt](https://www.pixelbeat.org/docs/numfmt.html)
