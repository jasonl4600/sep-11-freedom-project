# Tool Learning Log

Tool: **Kaboom**

Project: **Fate Platformer**

---

## 10/29/23:
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
---
## 12/3/23
Learning more elements in Kaboom
Kaboom introduces many components that can all be paired up with each other, so far during the work time I've spent on Monday this is what I learned
---
Platforms:
* Without a platform if you have a sprite that contains the body() component your sprite will have a physical body and without any platform it will keep falling.
* rect() renders a rectangle that accepts two arguments which include the width and height
* pos() meaning position can be given an x and y value like on a graph but in this case positioning the rectangle
* outline() self explanatory it assigns an outline to what you assign it with with a number like 4 being an outline of 4 pixels
* area() like body() but instead it gives something like a rectangle or whatever element it is a physical body which allows collisions with things like your sprite
* body({ isStatic: true }) What this does is makes the platform a static object meaning it doesn't move and that everything that doesn't move won't move past it either
* color(x, x, x) uses the RGB color system to assign colors to your platform or anything


add([
    rect(width(), 48),
    pos(0, height() - 48),
    outline(4),
    area(),
    body({ isStatic: true }),
    color(127, 200, 255),
])

Code here creates a platform using  all those components that is static in place and collideable with other physical elements like your sprite.
---
Condtions:
* Using an if statement we can create a condition where the sprite can only jump when it's grounded on the given platform
* We can use the component onKeyPress with an if statement where if that key is pressed the if statement will be ran
* onKeyPress("space", () => {
    if (bean.isGrounded()) {
        bean.jump();
    }
});
* Code above tells us that in the " " of onKeyPress is the key input
* The if statement runs the condition bean.isGrounded isGrounded is a function in the category of body that checks if the sprite is on a platform
* Now that the conditions are met it will run bean.jump(); which basically just allows the sprite to jump
---
## 12/10/23
* I watched a [video on a basic flappy bird tutorial](https://www.youtube.com/watch?v=hgReGsh5xVU&ab_channel=Replit) for roughly around 10 minutes today.
* I found out that instead of using my ide, I can use [replit](https://replit.com/) where kaboom is fully built in whereas using my ide I can only use the cdn link of Kaboomjs which I'm pretty sure is limited
* Tinkering a bit on the usage of Kaboom on Replit I found out you can customize, create, and search up sprites making it very accessible for the usage of making a game.
* Watching the video I now understand how width and height works more now that the Kaboom website didn't explain
```js
add([
    sprite("image", {width: width(), height: height()})
]);
```
This is the code used to create a background. What I didn't understand about width and height is how width: width() and height: height() works without numbers. It's just blank so what does it do? The video explains that if it's blank like that with paranthesis then it takes up the whole screen which is useful for adding something like a background.

I tip I also learned is that in the case of adding sprites they topple over each other so if you had a character and a background you want to add the background first and the character sprite next so the character sprite is "on top" of the background sprite. Basically so it overlays the background.

## 1/15/24

* Watched this [video](https://www.youtube.com/watch?v=4OaHB0JbJDI&t=2623s) on youtube for 20 minutes on just general components that can be used to make games on Kaboom
* Learned a new component addLevel() that allows you to create kind of a map layout for your game
```js
addLevel([
  "                                  ",
  "                                  ",
  "       @                          ",
  "                 ==               ",
  "                                  ",
  "===========================       "
])
```
* At first I didn't know what any of those symbols meant but after some more research I found out that " or ' being interchangeable are simply just spaces in the level that don't have anything in them like a block. 
* Your sprite/character is defined by the character @ which is placed wherever you want as long as it's in an empty space
* Finally == or xx being interchangeable as well represents a tile or the ground of your game which can be made into anything you want look wise as you can incorporate the ground tiles with sprites allowing you to make something like a grass block as the tile
* In the tile component you can also assign te component "solid" to make it an actual existing ground that a body wouldn't fall through as they technically are just placeholders that take up the layout until you assign something to it

## 3/4/24:

* Today I was continuing trying to create levels for my game which is the base for the whole game itself.
* I watched many videos on how to use addLevel() to create my level but none of them worked and equated to the element "solid", "width", and "height" not being defined. I really didn't know the issue here as all the videos that used addLevel() had no issues like that.
* I ended up searching up online "solid() not defined Kaboomjs" and got this [result](https://www.reddit.com/r/learnjavascript/comments/15t5d9b/kaboomjs_solid_is_not_defined/?rdt=54320) with a user online that has the same issue.
* Apparently Kaboom recently came out with a [new version](https://kaboomjs.com/blog/3000) of their code: Kaboom3000 and with the addition of this new version they removed and added certain features specifically, removed the element solid() which caused my level to not work.
```js
addLevel([
                "                          $",
                "                          $",
                "           $$         =   $",
                "  %      ====         =   $",
                "                      =    ",
                "       ^^      = >    =   &",
                "===========================",
            ], {
                // define the size of tile block
                width: 32,
                height: 32,
                // define what each symbol means, by a function returning a component list (what will be passed to add())
                tiles: {
                    "=": () => [
                        sprite("bean"),
                        area(),
                        solid()
                    ]
                }
            })
```

```js
addLevel([
                "                          $",
                "                          $",
                "           $$         =   $",
                "  %      ====         =   $",
                "                      =    ",
                "       ^^      = >    =   &",
                "===========================",
            ], {
                tileWidth: 32,
                tileHeight: 32,
                tiles: {
                    "=": () => [
                        sprite("bean"),
                        area(),
                        body({ isStatic: true }),
                    ]
                }
            })
```
* As you can see in the first set of code above everything is the same besides width, height, and solid compared to the 2nd set of code. This is because the component addLevel() and element solid are done differently and removed where you define height and width as tileheight/width and solid just being removed in general.

* This was a big issue for a while because the documentation on kaboom still uses height, width, and solid for the component addLevel() and nowhere does it mention these elements being removed unless you check the blog section with updates concerning the new version of kaboom.
* Now that I fixed a huge problem I have created a level and can use this important component to continue with my full game.

# 3/24/24:

* Having my level now I have a solid platform that I my player can walk and interact with. Because now I can add sprites and objects onto the level I decided I should learn collisions next or just updates from touching other sprites in general

* The first thing I wanted to try out was the element "update" specifically onUpdate meaning in the event such action is taken out the selected object would have the specific event in code outputted.

```js
player.onUpdate(() => {
    if (player.isHovering()) {
        player.color = rgb(0, 0, 255)
    } else {
        player.color = rgb()
    }
})
```
* This code above takes an existing global variable, "player" which is the sprite bean and uses a conditional to turn a event on and off which in this case is when the sprite is being hovered it will change into the hardcoded color and if it's not, the else statement will take place and give it no color (returning it to its original state).

* Next I wanted to try a event/update that interacts one object with another.
```js
player.onCollide("enemy", (enemy) => {
	destroy(enemy)
})
player.onCollideUpdate("enemy", () => {
})
```
* This code is supposed to destroy the sprite with the tag enemy which is just bean2 in my sprites but I was given the error that destroy was not defined?
* I'm still not sure towards why this is the case but I'm pretty sure it's because of the new Kaboom version as destroy is on the Kaboomjs website documentation but might not be on the new version.





<!-- 
* Links you used today (websites, videos, etc)
* Things you tried, progress you made, etc
* Challenges, a-ha moments, etc
* Questions you still have
* What you're going to try next
-->
