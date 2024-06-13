# Entry 5
##### 5/1/24

# Continuation of MVP

Previously I have created my singular level which was part of my game. I decided that for a platformer I should really have more than one level. At this point I wasn't so sure how to create and go to different levels using the [KaboomJs](https://kaboomjs.com/#kaboom) documentation. I searched up a video to something similar to what I was trying to do and followed which turned out to be helpful. This [video](https://www.youtube.com/watch?v=37rASpfnCCM&t=2606s) had a great guide and explanation through many different Kaboom concepts that I could implement towards my game.

Previously my level layout looked something like this:

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

Now the issue with this level is that I am adding one level and only one level. Where I want to create more than one using addLevel([]) would not work. This is where the video I mentioned earlier explained and showed me how you create a variable that holds onto multiple different levels seperated by commas like this:

```js
const layout = [
                [
                "= = = = = = = = = = = = = = =",
                "                             ",
                "=                           =",
                "                             ",
                "=                           =",
                "                             ",
                "=                           =",
                "                             ",
                "=                           =",
                "                             ",
                "=                           =",
                "                             ",
                "=                           =",
                "                             ",
                "=                           =",
                "                             ",
                "=                           =",
                "                             ",
                "=            # # #          =",
                "                             ",
                "=            # @ #          =",
                "                             ",
                "=            # # #          =",
                "                             ",
                "=                           =",
                "            *   +            ",
                "=                           =",
                "                             ",
                "=                        -  =",
                "                             ",
                "=                           =",
                "                             ",
                "= = = = = = = = = = = = = = =",
                ],
]
```

In my code there is also another wall of this map layout for the second level but trying to not make this a text wall I create multiple of these levels with changes to the layout and more.

Continuing with how I would move onto these levels like entering the next level when a condition is met, the video I watched also goes through this. Now using the variable we created, we will take that and put it in a scene so they will all be existing in that current scene meaning all levels will be there.

```js
scene("game", ({level_id, kills} = {level_id: 0, kills: 0}) => {
                const level = addLevel(layout[level_id ?? 0], mapItems)
```

Now I want to create a condition for moving onto the next level. What I did was add a item, the philostone, which needs to be collected and collide with another object, Klaris, to move onto the next level.


```js
player.onCollide("klaris", () => {
               if(philostone){
                    if (level_id + 1 < layout.length) {
                        go("game",{
                            level_id: level_id + 1,
				            kills: kills,
                        })
                    } else {
                        go("win")
                    }
               }
            })
let philostone = false
player.onCollide("philostone", (key) => {
    destroy(key)
    philostone = true
})
```
What this block of code did for me was in summary collect the philostone and run a condition where the philostone is held in order to move onto the next level by touching Klaris.

# Next stage

Now that I've gotten multiple levels down and a system that lets me move onto said levels. The finishing touch for my mvp would be to actually design the levels. So far I have created a baseplate with components and functions that work but not the physical design that you would see in game. In short all the functions work but I haven't laid them out. In order to finish my MVP I will be designing the actual levels.


[Previous](entry04.md) | [Next](entry06.md)

[Home](../README.md)