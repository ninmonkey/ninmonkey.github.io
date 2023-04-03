
- [GH Repo List Json Fields](#gh-repo-list-json-fields)
  - [1](#1)
  - [2](#2)
  - [2 : default output](#2--default-output)


## GH Repo List Json Fields

### 1

```ps1
# capture by using:
gh run list | %{ 
   $_ -split '\t' -join ' | ' 
   | Join-String -op '| '  -os ' |'
} | Join-String -sep "`n"
```

~~~pipescript{
gh run list | %{ 
   $_ -split '\t' -join ' | ' 
   | Join-String -op '| '  -os ' |'
} | Join-String -sep "`n"
}~~~

### 2 

```ps1
# capture by using:
$isFirst = $true
gh run list | ForEach-Object { 
    $segments = $_ -split '\t'
    $colCount = $segments.count   
    $segments | Join-String -op '| ' -os ' |' -sep ' | '
    if ($IsFirst) { 
        $IsFirst = $false
        @('-' * $colCount -join '' -split '') # column row
        | Join-String -sep ' | '
    }

} | Join-String -sep "`n"
```

~~~pipescript{

Push-Location -stack 'test.export' 'H:\github_fork\Pwsh\PowerShellGuide'
$isFirst = $true
gh run list | ForEach-Object { 
    $segments = $_ -split '\t'
    $colCount = $segments.count   
    $segments | Join-String -op '| ' -os ' |' -sep ' | '
    if ($IsFirst) { 
        $IsFirst = $false
        @('-' * $colCount -join '' -split '') # column row
        | Join-String -sep ' | '
    }

} | Join-String -sep "`n"
Pop-Location -stack 'test.export'
}~~~

### 2 : default output

```ps1
Push-Location -stack 'test.export' 'H:\github_fork\Pwsh\PowerShellGuide'
$stdout =  gh run list 
$stdout
Pop-Location -stack 'test.export'
```
output
```tsv
~~~pipescript{ 
    Push-Location -stack 'test.export' 'H:\github_fork\Pwsh\PowerShellGuide'
    $stdout =  gh run list 
    $stdout
    Pop-Location -stack 'test.export'
}~~~
```