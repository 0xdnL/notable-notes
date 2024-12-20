---
tags: [linux]
title: unicode
created: '2023-12-06T11:58:13.706Z'
modified: '2024-12-05T08:58:12.917Z'
---

# unicode

> computing industry standard designed to consistently encode, represent, and handle text expressed in most of the world's writing systems

It provides a unique number (code point) for every character, no matter the platform, program, or language, facilitating the global exchange of text and data

## usage

```sh
echo -e "\u2713"  # You can use the echo command along with the Unicode sequence to display a Unicode character. For example: This command will print a checkmark (✔).

printf "\u2600\n" # The printf command can also be used to print Unicode characters. For example: This command will print a sun emoji (☀).

echo with UTF-8 Encoding:

echo -e "\xe2\x98\x83"      # You can use the echo command with UTF-8 encoded characters. For example: This command will print a snowman emoji (☃).



echo -e "\u2665" > unicode_file     # create a file containing Unicode characters
cat unicode_file

This will create a file with a heart symbol (♥) and then display its content using cat.


heart_symbol=$'\u2665'
echo $heart_symbol        # print a heart symbol (♥) 🍕
```

[[bash echo]], [[bash printf]]

## encoding

UTF-8 - `Unicode Transformation Format – 8-bit`
UTF-16
UTF-32

[[url encoding]]

## see also

- [[uniname]]
- [[ascii]]
- [[gnu readline]], [[bash bind]]
- [[macos keyboard shortcuts]]
- [[nvim]]
