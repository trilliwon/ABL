---
layout: post
title:  "Suspend or Resume user touch events."
date:   2019-04-09 10:58:00 +0900
tags: [iOS]
---

> Tells the receiver to suspend the handling of touch-related events.

```
UIApplication.shared.beginIgnoringInteractionEvents()
```

### Discussion

You typically call this method before starting an animation or transition. Calls are nested with the endIgnoringInteractionEvents() method.

---

> Tells the receiver to resume the handling of touch-related events.

```
UIApplication.shared.endIgnoringInteractionEvents()
```

### Discussion

You typically call this method when, after calling the beginIgnoringInteractionEvents() method, the animation or transition concludes. Nested calls of this method should match nested calls of the beginIgnoringInteractionEvents() method.