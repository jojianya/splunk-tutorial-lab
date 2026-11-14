# SPL Cheatsheet

| Command | Syntax | Example |
| --- | --- | --- |
| `stats` | `stats <func>(<field>) [as <alias>] by <field>` | `... \| stats count by clientip` |
| `top` | `top [limit=<n>] <field>` | `... \| top limit=10 clientip` |
| `rex` | `rex "<regex with (?<name>...)>"` | `... \| rex "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"` |
| `timechart` | `timechart [span=<time>] <func>` | `... \| timechart span=1h count` |
| `bin` | `bin _time span=<time>` | `... \| bin _time span=5m` |
| `eval` | `eval <new_field>=<expression>` | `... \| eval kb=bytes/1024` |
| `where` | `where <boolean expression>` | `... \| where count >= 10` |
| `dc` | `dc(<field>)` returns the number of distinct values | `... \| stats dc(user) as unique_users by src_ip` |
| `sort` | `sort <+-\|field>` (`-` = descending) | `... \| sort -count` |
