# bubbling-and-capture
My updated version of MDN's bubbling and capture example.

The original comes from MDN's "Introduction to events" tutorial in the "JavaScript building blocks" course.
(Link: https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events - accessed 23/11/2021)

The original code is presented in the "Bubbling and capturing explained section".

This example presents 5 nested div elements. The user can click on any of these divs, and a series of messages log the various stages of the bubbling and capture process. However, there is a slight flaw: when the "clear output" button is clicked, the text is not fully cleared - the messages "BUBBLING PHASE: [object HTMLDocument]" and "BUBBLING PHASE: [object Window]" remain. Although the clear button has an event handler that sets the content of the log section's innerHTML to be equal to "", the events bubble up to the HTML document object and the window (because the button exists inside both these environments, obviously) and their event text is then added back into the log section after it has been cleared.

Fortunately, there is an easy way to fix this problem, and it is presented in the next section of the tutorial: "Fixing the problem with stopPropagation()". (In this case the "problem" refers to an example of a video that disappears when its play button is pressed, but it could easily refer to the issue of the lingering log messages). To prevent the log messages for the bubbling phases of the HTML document and the window always being present, it is simply necessary to add an "evt" argument to the clearOutput function and then call "evt.stopPropagation()" inside the clearOutput function.

As a further minor change, I have replaced "evt.currentTarget" with "evt.currentTarget.toString().slice(8, -1)" in the "gphase(evt)" function to remove "[object " and "]" from the output of this function. (This is so that the output messages become "BUBBLING PHASE: HTMLDocument" instead of "BUBBLING PHASE: [object HTMLDocument]", for example.
