---
title: "Non-printable keys will soon stop firing `keypress` event"
date: "2018-03-03T04:49:00-05:00"
categories: ["dom"]
tags: []
versions: ["60"]
statuses: "affecting"
references:
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1440189"
      title: "Bug 1440189 - Stop dispatching keypress event on web content in Nightly"
    - url: "https://bugzilla.mozilla.org/show_bug.cgi?id=1442528"
      title: "Bug 1442528 - Nightly 2018-03-01 broke keyboard handling in Google Docs"
    - url: "https://groups.google.com/d/topic/mozilla.dev.platform/wW9el-i5mtA/discussion"
      title: "Intent to stop dispatching \"keypress\" event for non-printable keys and key combinations in Nightly and early Beta"
---
In order to follow the [UI Events spec](https://w3c.github.io/uievents/) and other browsers' behaviour, Firefox will stop dispatching the `keypress` event for non-printable keys and key combinations in the near future.

[Non-printable keys](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/keyCode#Non-printable_keys_(function_keys)) are function keys like Home, End, Tab, Escape, Backspace, Page Down, arrows, etc. Non-printable key combinations include Ctrl+A, Alt+G, Command+Shift+M and so on. Web developers should be using the `keydown` event instead to handle those keys.

An exception is the Enter key; pressing Enter with no modifiers, Shift+Enter or Ctrl+Enter will fire the `keypress` event as before, which is invalid in the current spec but compatible with other browsers.

This change has been made to the Nightly and early Beta/DevEdition channels as of Firefox 60. Other channels will also adopt the standard-compliant behaviour once compatibility issues on major sites are solved. Currently, some keyboard shortcuts on *Google Docs* and *Google Sheets* are known to be broken.