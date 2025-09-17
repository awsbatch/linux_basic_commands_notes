# what is `less` and `more` command.
both `less` and `more` are pagers in Linux/Unix systems: tools to view long text output one screen at a time. But they differ in power and usage.

---
## more command
- Basic pager (older, simpler).
- Shows one screen at a time and lets you move forward only (line by line or page by page).
- Very limited navigation.

**👉 Common use cases:**

- Quickly view logs or config files if you only need to scroll down.

### Example:
```
cat bigfile.log | more
```
```
more /etc/ssh/sshd_config
```

### Commands:

`SPACE`  → next page

`ENTER`  → next line

`q`      → quit

---
## less command

- Advanced pager (newer, more feature-rich).
- Lets you move forward and backward in a file.
- Supports searching (/pattern), scrolling, jumping to line numbers, etc.
- Does not load the whole file into memory (good for very large logs).

**👉 Common use cases:**

-  Inspecting huge log files.

-  Searching inside configuration or code.

### Example:
```
less /var/log/syslog
```
```
cat /var/log/syslog | less
```

### Commands:

`SPACE` → next page

`b` → previous page

`/word` → search forward

`?word` → search backward

`n` → repeat search

`g` → go to start, G → go to end

`q` → quit

## Key Differences
| Feature                  | `more`       | `less`              |
| ------------------------ | ------------ | ------------------- |
| Navigation               | Forward only | Forward & backward  |
| Search                   | No           | Yes (`/pattern`)    |
| Performance on big files | Basic        | Very efficient      |
| Usability                | Minimal      | Powerful & flexible |
| Age                      | Older        | Modern replacement  |


## 👉 Rule of thumb:

  -  Use less when exploring logs, configs, or code (you almost always want searching & backward navigation).

  -  Use more only in minimal environments (like very small containers or busybox) where less may not be installed.

**⚡ Fun fact: the name joke is: “less is more” — because less is basically a supercharged version of more. 😄**
