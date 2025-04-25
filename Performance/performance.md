# Web performance

## Core web vitals (CWV)
Core web vitals are ... metrics for measuring performance in general.
These metrics influence page rank as Google uses them for ranking search results,
but also have a direct correlation with customer satisfaction, conversion rates and
revenue so can be worth investing in.

P90 explained: @todo

### Longest contentful paint (LCP)
How long the page takes to load. The network load times usually?
Improved by:
- reducing size of the requested resources. For example bundle splitting (ie. smaller js bundles load) and deferring/lazy loading images
- Caching: Content delivery network (CDN), service workers maybe?

This video offers a systematic approach for auditing LCP and other CWV using the Lighthouse dev tool: https://www.youtube.com/watch?v=5fLW5Q5ODiE

### Interaction to next paint
Measures the responsiveness between interactions on the page. When a user is typing or clicking, does the page lag in response.
Frames per second can help identify this quantitatively rather than just the 'feeling' of lag. Open chrome dev tools, ctrl-shift-p
or cmd-shift-p, and type 'fps' to show the fps. A signficant drop will indicate poor INP. FPS will drop because javascript code is
single threaded on the browser (things can't run concurrently) and so when an onclick causes a while loop or some js code that takes
a while to execute, this will block the UI from updating until after it is finished execution.

Note: mobile devices generally experience worse INP because they are lower end hardware compared to desktops. It can help to use the
mobile device mode in chrome devtools or throttling CPU simulation in the dev tools to diagnose issues.

It can be improved by deferring tasks that don't need to run before the next paint, after an interaction event occurs.

Great resource explaining some optimisation techniques, including scheduler.yield to break up long tasks, and abort controllers for 
aborting long tasks early:
https://www.youtube.com/watch?v=KZ1kxzsJZ5g

Another great video for helping to get comfortable with the performance tab: https://www.youtube.com/watch?v=cmtfM4emG5k

### Memory leaks:
Memory leaks can cause applications to eventually crash because no memory is left in the heap to store new objects.
This occurs in the browser because although js has a built in garbage-collector, by maintaining references to objects in memory, the garbage collector will not clean this objects up, despite them not actually being used in some cases. The chrome developer memory tab can help diagnose these problems. https://www.youtube.com/watch?v=YDU_3WdfkxA
