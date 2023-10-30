# Tool Learning Log

Tool: **Kaboom**

Project: **Fate Platformer**

---

10/29/23:
* First I set up Kaboom by using the CDN, I simply did this by going to the setup document and pasting this into a index.html file I created for testing Kaboom:
``` js 
<script type="module">

// import kaboom lib
import kaboom from "https://unpkg.com/kaboom@3000.0.1/dist/kaboom.mjs";

// initialize kaboom context
kaboom();

// add a piece of text at position (120, 80)
add([
    text("hello"),
    pos(120, 80),
]);
</script>
```
* I also tinkered with the Kaboom Playground, it lets you choose different elements and components and gives you basic code that uses that specific element/component which you can change.
* I played around with the gravity component by changing the value of gravity which is a value that changes the rate an object moves in by pixels pers second
* I also tinkered by changing the key to jump instead of having space as the key I changed it to w
* Another thing I tinkered with is an ai element where you have an enemy that follows you and shoots you every so often which would kill you.
* I tinkered by changing some values and aspects of the entity making it faster and the bullets it shoots more accurate making it smarter and stronger.

X/X/X:
* Text


<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
