
## GH Repo List Json Fields

```ps1
# capture by using:
gh repo list --json 2>&1
```
~~~pipescript{
$BinGH = Get-Command 'gh' -CommandType Application
| Select-Object -First 1
if (-not $BinGH) {
    throw 'missing required "gh" command' }

$q = & $BinGH repo list --json 2>&1
| Select-Object -Skip 1
| Join-String -sep ','

$q -replace '\s+', '' -split ','
| Sort-Object
| Join-String -sep "`n" -f '- {0}'
}~~~