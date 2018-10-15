---
title: Error: tool 'xcodebuild' requires Xcode... on macOS
categories: [Mac]
tags: [command line, terminal, Xcode]
---

If you get the following error with `npm install`

```
 xcode-select: error: tool 'xcodebuild' requires Xcode, but active developer directory'/Library/Developer/CommandLineTools' is a command line tools instance
```

then to fix it try

1. (optional) Install `Xcode` - go to the AppStore and [download the Xcode](https://itunes.apple.com/us/app/xcode/id497799835).
2. Point the `xcode-select` developer directory to the appropriate directory from within `Xcode.app`. To do this, run

```bash
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```
