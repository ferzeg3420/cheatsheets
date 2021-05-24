# MOVEMENT is life


| Char sequence | What it does |
| ----------- | ----------- |
| gg | first line of the file. |
| `^b` | up one page. |
| `^u` | up 1/2 page. |
| h, j, k, l | cursor left, down, up, and to the right. |
| 0 | beginning of the line. |
| $ | end of the line. |
| B, b | previous word. |
| E, e | end of the word  |
| w | beginning of the next word. |
| `^d` | down 1/2 a page. |
| `^f` | down 1 page. |
| G | end of the file. |

# Location, Location, Location

| Char sequence | What it does |
| ----------- | ----------- |
| zz | center at cursor. |
| zt | at the top of the screen. |
| zb | at the bottom. |

# I ain't no quitter

| Char sequence | What it does |
| ----------- | ----------- |
| `:aq`            | quits w/o saving. |
| `:wq`            | quits with writing/saving. |
| `:q`             | quit after asking questions. |

# DELETING fluff

| Char sequence | What it does |
| ----------- | ----------- |
| N dd           | deletes N lines from the cursor. |
| D              | Deletes this line up to the `\n` character. |
| i, a           | Inserts text at and after the cursor. |

# SEARCHING for life's meaning

| Char sequence | What it does |
| ----------- | ----------- |
| `/`              | regex forward find. n and p to cycle through finds. |
| `?`              | regex backward find. n and p like above. |

# the UNDOing project

| Char sequence | What it does |
| ----------- | ----------- |
| u              | undo |
| `^r`             | redo |

# MISCellaneous

| Char sequence | What it does |
| ----------- | ----------- |
| `^v I //`        | commenting: `^v` move around, then press I, and `//` |
| `:help`          | manual. |
| `^]`         | follow a vim link, sth in between `||` e.g., `|link|` |

