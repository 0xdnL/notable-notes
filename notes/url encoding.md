---
title: url encoding
created: '2024-12-05T08:44:53.169Z'
modified: '2024-12-05T08:55:33.679Z'
---

# url encoding

[rfc-3986 percent-encoding](https://www.rfc-editor.org/rfc/rfc3986#section-2.1)

term percent-encoding should be preferred, as encoding applies to:

- URLs (`Uniform Resource Locators`)
- URIs (`Uniform Resource Identifiers`)
- URNs (`Uniform Resource Names`)


```
unreserved characters can be encoded, but should not be encoded
unreserved characters are:

A B C D E F G H I J K L M N O P Q R S T U V W X Y Z a b c d e f g h i j k l m n o p q r s t u v w x y z 0 1 2 3 4 5 6 7 8 9 - _ . ~
```

```
reserved characters have to be encoded only under certain circumstances
reserved characters are:

! * ' ( ) ; : @ & = + $ , / ? % # [ ] 
```

Common characters after percent-encoding ([[ascii]] or [[unicode]] UTF-8 based)

```
␣ 	  " 	  % 	  -     .     <     >     \     ^     _     `     {     |     }     ~     £       €
%20 	%22 	%25 	%2D 	%2E 	%3C 	%3E 	%5C 	%5E 	%5F 	%60 	%7B 	%7C 	%7D 	%7E 	%C2%A3 	%E2%82%AC
```

## see also

- [[jq]]
- [[curl]]
- [[bash echo]]
