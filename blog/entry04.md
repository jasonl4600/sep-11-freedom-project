# Entry 4
##### 3/28/24

# Continuing with my tool

Continuing with my tool I started adding and refactoring some of my code to really just create some overall improvements for the game while adding some content to it as well. Many Youtube videos that go over Kaboom content are outdated so recetnly I've just been relying on the [Kaboom documentation instead.](https://kaboomjs.com/)

From the last entry I've changed the level part of my game to be more fitting and less messy. Previously the code looked like this:
```js
addLevel([
                "                          $",
                "                          $",
                "           $$         =   $",
                "  %      ====         =   $",
                "                      =    ",
                "       ^^      = >    =   &",
                "===========================",
```

Now I've changed it to be more like this:
```js
addLevel([
                "                          $",
                "                          $",
                "                          $",
                "                          $",
                "                           ",
                "                          &",
                "                          &",
                "                          &",
                "                          &",
                "                           ",
                "                           ",
                "                           ",
                "                           ",
                "                           ",
                "                           ",
                "                           ",
                "        ^^             =   ",
                "        = = =              ",
                "                 >     =   ",
                "                           ",
                "                       =   ",
                "                           ",
                "= = = = = = = = = = = = = =",
```
Although it definitely looks a lot bigger and unnecessary compared to my old one there were many changes that just make it visually look better. First the level actually starts at the bottom of the screen. What I mean by this is unlike the old code the level (platform) you stand on is not just floating in the air. Another change I didn't think of last time was to space out the "=". The equal marks stand for a sprite block that is just the floor. Not having them spaced out kind of mashes them together halfway. Adding a space to each equal sign makes it so each block starts right at the end of the last one. In this I've created a more visually appealing level.

Next, just another visual but important kind of content I've added is a way for the camera to follow the character you're controlling. I looked for the component to follow your character on the [Kaboom documentation](kaboomjs.com). The component is called camPos and it stands for camera position. This component is how you set the camera position of the game.

```js
player.onUpdate(() => {
    camPos(player.pos)
})
```
Here is the code necessary to allow your camera to follow the character or any sprite depending on how you set it. Player in this case is the tag/name of my sprite that is being controlled. When there is any action that involves the player runs like moving the camera position will be on the player. Although before doing this I made a little bit of a mistake. The code above is perfectly fine on its own but for 5 minutes I was super confused why it didn't work.

```js
const player = add([
                sprite("bean"),
                pos(80, 40),
                area(),
                body(),
                health(8)

                player.onUpdate(() => {
                camPos(player.pos)
            })
            ])
```

As you can see or may not see, I put the camPos component **INSIDE** of an already existing component where I added my character. This was generally a really small mistake but it creates an error that bugs out the whole game.

# MVP

After this, I can think of 3 more things I need to learn/add to my game that gives me my MVP. I need to be able to learn how to implement enemies that move. I have not yet been able to understand how to get enemies to move around/follow you. I plan to have them destroy your character on touch but if you jump on their head then they get destroyed instead. I'm also thinking of adding some kind of score either for collecting coins or defeating enemies. If I don't end up doing that then I'll be adding multiple levels. It will be implemented in a way where you reach a certain area and another "level" loads in with different obstacles/enemies that all work in the same way.

The top priority for now is learning how to direct enemy positions to move towards your character.

[Previous](entry03.md) | [Next](entry05.md)

[Home](../README.md)