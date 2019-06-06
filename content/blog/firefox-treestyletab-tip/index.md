---
title: "Optimizing your Tree Style Tab experience with groups"
description: ""
date: "2019-06-05T22:13:51.542392"
---

If you're using [Firefox](https://www.mozilla.org/en-US/firefox/new/) and have the [Tree Style Tab](https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/) *(TST)* extension installed, you can create a TST group by navigating to the following URL: 

```
about:treestyletab-group?title=MyGroup
``` 

TST groups are useful for organization purposes because they give you an *empty*
space to throw bunch of browser tabs at.

If you're on Linux or Mac you can speed up the process of creating a TST group
by copying the following into an executable shell script and placing it
in your `$PATH`:

```bash
#!/usr/bin/fish
#
# Usage: tabgroup ARG1 ARG2...ARGN
#
# Purpose: Open up one or more temporary treestyletab
# groups in Firefox with the specified names.

function tabgroup
  if not count $argv > /dev/null
    return
  end
  for title in $argv
    firefox "about:treestyletab-group?title=$title"
  end
end
```

**Note:** Make sure you have [fish shell](https://fishshell.com/) installed
otherwise you won't able to run this script.

Once you have the script ready to go, you can pop open a terminal and create either:
- **A single TST group:** `tabgroup mytabgroup`  
- **Multiple TST groups:** `tabgroup groupone grouptwo groupthree`