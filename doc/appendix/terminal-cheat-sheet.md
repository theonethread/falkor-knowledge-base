# **Terminal Cheat Sheet**

## **Table of Contents**

1. [Bash to PowerShell](#bash-to-powershell "View")

## **Bash to PowerShell**

| bash | PowerShell | notes |
| :-- | :-- | :-- |
| `which <command>` | `Get-Command <command>` |  |
|  | `Get-Command <command> \| Select-Object -ExpandProperty Definition` | for \*nix-style output |
| `rm -rf <path>` | `Remove-Item -Recurse -Force <path>` |  |
| `find <path> -type f -iname <pattern>` | `Get-ChildItem -Path <path> -File -Filter <pattern> -Recurse` |
| `… \| grep <pattern>` | `… \| Select-String -Pattern <pattern>` |  |
|  | `… \| Out-String -Stream \| Select-String -Pattern <pattern>` | based on return value |
| `command &> file` | `command > file 2>&1` | `&>` does not work in PowerShell, note redirection order |
| `time <command>` | `Measure-Command <command>` |  |
| `export NODE_OPTIONS="--<option>=<value>"` | `$Env:NODE_OPTIONS="--<option>=<value>"` |  |
| `NODE_OPTIONS="--<option>=<value>" <command>` | `$Env:NODE_OPTIONS="--<option>=<value>"; <command>; $Env:NODE_OPTIONS=$null` | can't set environment variables for a single command in PowerShell |

---

_©2020-2023 Barnabas Bucsy - All rights reserved._
