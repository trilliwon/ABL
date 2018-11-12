---
layout: post
title:  "Swift canImport"
date:   2018-11-12 01:16:00 +0900
tags: [Swift, Tips]
---


- proposal [SE-0075)](https://github.com/apple/swift-evolution/blob/master/proposals/0075-import-test.md)

```swift
#if canImport(UIKit)
// UIKit-based code
#elseif canImport(Cocoa)
// OSX code
#else
// Workaround/text, whatever
#endif

```

