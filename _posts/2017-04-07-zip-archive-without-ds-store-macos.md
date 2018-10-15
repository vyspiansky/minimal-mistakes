---
title: Make a Zip Archive without a .DS_Store file on macOS
categories: [Mac]
tags: [Zip, macOS, terminal]
---

Let’s compress folder (current one) without the `.DS_Store` file

```bash
zip -r <name>.zip . -x "*.DS_Store"
```

**Note!** `.DS_Store` is a file that stores custom attributes of its containing folder, such as the position of icons or the choice of a background image.