

## GH Repo List Json Fields

### 1

```ps1
# capture by using:
gh run list | %{ 
   $_ -split '\t' -join ' | ' 
   | Join-String -op '| '  -os ' |'
} | Join-String -sep "`n"
```

| completed | success | pages build and deployment | pages-build-deployment | main | dynamic | 4578356726 | 57s | 2d |
| completed | success | pages build and deployment | pages-build-deployment | main | dynamic | 1896618181 | 51s | Feb 25, 2022 |

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

| completed | success   | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4496465924 | 54s   | 10d |
| --------- | --------- | ------------------------------------------------------------- | ---------------------- | ------------------------ | ------- | ---------- | ----- | --- |
| completed | success   | Merge pull request #61 from mdowst/namespace-and-dot-net      | Build PowerShell Guide | PowerShell-Guide-Updates | push    | 4496461634 | 56s   | 10d |
| completed | cancelled | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4496461553 | 48s   | 10d |
| completed | success   | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4496441645 | 54s   | 10d |
| completed | cancelled | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4496437528 | 46s   | 10d |
| completed | success   | Adding courses to attributes (re #69)                         | Build PowerShell Guide | PowerShell-Guide-Updates | push    | 4496437484 | 53s   | 10d |
| completed | success   | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4496416900 | 1m7s  | 10d |
| completed | cancelled | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4496413516 | 42s   | 10d |
| completed | success   | Adding ValidateScript topic (Fixes #71)                       | Build PowerShell Guide | PowerShell-Guide-Updates | push    | 4496413481 | 58s   | 10d |
| completed | success   | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4432995014 | 1m14s | 17d |
| completed | cancelled | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4432994364 | 22s   | 17d |
| completed | success   | Updating export (sorting courses and topics by name) (re #69) | Build PowerShell Guide | PowerShell-Guide-Updates | push    | 4432992371 | 52s   | 17d |
| completed | cancelled | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4432992293 | 29s   | 17d |
| completed | success   | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4432976356 | 1m4s  | 17d |
| completed | success   | Updating TopicsByLevel (removing table (re #69)               | Build PowerShell Guide | PowerShell-Guide-Updates | push    | 4432976311 | 54s   | 17d |
| completed | success   | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4432969908 | 55s   | 17d |
| completed | cancelled | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4432969169 | 18s   | 17d |
| completed | success   | Updating Types (sorting .AllTopics) (re #69)                  | Build PowerShell Guide | PowerShell-Guide-Updates | push    | 4432967321 | 52s   | 17d |
| completed | cancelled | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4432967263 | 29s   | 17d |
| completed | cancelled | pages build and deployment                                    | pages-build-deployment | PowerShell-Guide-Updates | dynamic | 4432964185 | 45s   | 17d |

### 2 : default output

```ps1
Push-Location -stack 'test.export' 'H:\github_fork\Pwsh\PowerShellGuide'
$stdout =  gh run list 
$stdout
Pop-Location -stack 'test.export'
```
output
```tsv
completed	success	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4496465924	54s	10d completed	success	Merge pull request #61 from mdowst/namespace-and-dot-net	Build PowerShell Guide	PowerShell-Guide-Updates	push	4496461634	56s	10d completed	cancelled	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4496461553	48s	10d completed	success	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4496441645	54s	10d completed	cancelled	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4496437528	46s	10d completed	success	Adding courses to attributes (re #69)	Build PowerShell Guide	PowerShell-Guide-Updates	push	4496437484	53s	10d completed	success	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4496416900	1m7s	10d completed	cancelled	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4496413516	42s	10d completed	success	Adding ValidateScript topic (Fixes #71)	Build PowerShell Guide	PowerShell-Guide-Updates	push	4496413481	58s	10d completed	success	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4432995014	1m14s	17d completed	cancelled	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4432994364	22s	17d completed	success	Updating export (sorting courses and topics by name) (re #69)	Build PowerShell Guide	PowerShell-Guide-Updates	push	4432992371	52s	17d completed	cancelled	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4432992293	29s	17d completed	success	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4432976356	1m4s	17d completed	success	Updating TopicsByLevel (removing table (re #69)	Build PowerShell Guide	PowerShell-Guide-Updates	push	4432976311	54s	17d completed	success	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4432969908	55s	17d completed	cancelled	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4432969169	18s	17d completed	success	Updating Types (sorting .AllTopics) (re #69)	Build PowerShell Guide	PowerShell-Guide-Updates	push	4432967321	52s	17d completed	cancelled	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4432967263	29s	17d completed	cancelled	pages build and deployment	pages-build-deployment	PowerShell-Guide-Updates	dynamic	4432964185	45s	17d
```
