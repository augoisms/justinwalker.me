---
layout: post
title: C# - String to Title Case
date: '2015-04-10 23:44:43'
tags:
- c
- regex
---

I was recently given a bunch of data to import where the names of businesses where all capitalized and I needed to store them in title case. `TextInfo` has a `ToTitleCase` method but it does not account for special characters (e.g. "O'BRIAN" or "BEST-COFFEE").

I ended up writing a string extention method where I first run `ToTitleCase` then apply regex to look for letters following special characters. This also catches words with `'s` at the end so I run another regex replace to fix the possesive S.

I tried to combine the regex expressions to look for "letters after special characters except if they are `'s` at the end of a word." I had no luck though and ended up two operations.


```csharp
public static string ToTitleCase(this string s)
{
    // make the first letter of each word uppercase
    var titlecase = CultureInfo.InvariantCulture.TextInfo.ToTitleCase(s.ToLower());
    // match any letter after an apostrophe and make uppercase
    titlecase = Regex.Replace(titlecase, "[^A-Za-z0-9 ](?:.)", m => m.Value.ToUpper());
    // look for 'S at the end of a word and make lower
    titlecase = Regex.Replace(titlecase, @"('S)\b", m => m.Value.ToLower());
    return titlecase;
}
```