## Permissions

* `antispamnames.immune` -- Allows player to not being checked by this plugin

##  Configuration
Just specify 'Spam keyword blacklist' with words (or domain extensions) you want to avoid. These words will be replaced with 'Replace for spam' expression.
You can also control fake admin players. Use 'Admin name blacklist' to specify words to avoid for non-admin players. It will ignore real administrators of course.

Now supports regex! Default regex matches `IP`, `port`, `domain` with `subdomains` and `admin` word.
Regex list check is case insensitive by the design (at least for english). Replaces founded with `Replace for spam`.
All checks are disabled by default, so you can install plugin safely and then change default config to your needs.
You probably want to try enabling only regex list first, as it may be all you need.
Afterwards you can always enable additional checks if needed.

```json
{
  "Admin name blacklist": [
    "Administrator",
    "Admin"
  ],
  "Allow check name for spam regex list": false,
  "Check admin names": false,
  "Check spam names": false,
  "Print to log all name changes": true,
  "Replace for admin": "Player",
  "Replace for spam": "Spam",
  "Replace if empty (whole name filtered)": "Good name",
  "Spam keyword blacklist": [
    ".money",
    ".ru",
    ".com",
    ".pl",
    ".gg",
    ".de",
    ".net",
    "www.",
    ".org",
    ".info",
    ".cz",
    ".sk",
    ".uk",
    ".cn",
    ".nl",
    ".store",
    ".shop"
  ],
  "Spam regex list": [
    "(?:(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\\.){3}(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)",
    "(:\\d{3,5})",
    "([类a4][匿d][天m][辱i1][晚n])",
    "(https|http|ftp|):\\/\\/",
    "((\\p{L}+|[0-9]+)+\\.)+(com|org|net|int|edu|gov|mil|ch|cn|co|de|eu|fr|in|nz|ru|tk|tr|uk|us)",
    "((\\p{L}+|[0-9]+)+\\.)+(ua|pro|io|dev|me|ml|tk|ml|ga|cf|gq|tf)"
  ]
}
```

## API

```cs
string GetClearText(string text, List<string> regexList, string replacement)
//will return string with all regexList matches replaced with passed replacement
/*
myDirtyText = "Administrator"
replacement = "Spam"
List<string> regexList = new List<string>() {"([类a4][匿d][天m][辱i1][晚n])"}
var myClearedText = GetClearText(myDirtyText, regexList, replacement)
// myClearedText will be = "Spamistrator"
*/
```

I would appreciate any feedback or ideas to improve this plugin.