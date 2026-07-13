## Make the clicker

Add something to click and a score that goes up when you click it.

> [!TASK]
>
> Delete the cat sprite.
>
> ![Deleting a sprite with the bin icon on its thumbnail.](images/delete-sprite.png)

> [!TASK]
>
> Add your own sprite with **Choose a Sprite** (library, **Upload**, or
> **Paint**). The pizza shop uses a pizza.
>
> ![The Choose a Sprite button in the bottom-right of the Scratch editor.](images/sprite-choose.png)

> [!TASK]
>
> Make a variable called `pizzas`{:class="block3variables"} and tick it so the
> player can see their score.
>
> ![The Make a Variable button in the Variables palette.](images/make-a-variable.png)
>
> ![A ticked variable checkbox showing the value on the stage.](images/variable-checkbox.png)

> [!TASK]
>
> Make your sprite clickable, so each click makes a pizza.
>
> ```blocks3
> when this sprite clicked
> change [pizzas v] by (1)
> ```

Click your sprite. The `pizzas`{:class="block3variables"} score goes up.

> [!TASK]
>
> Add a sound so a click feels good. Open the **Sounds** tab, click the speaker
> icon, and pick something short. Then add it to the top of your script.
> Use `start sound`{:class="block3sound"} in this project, not
> `play sound until done`{:class="block3sound"}, so the sound starts without
> holding up the rest of the program.
>
> ![The Sounds tab at the top-left of the editor.](images/sounds_tab.png)
>
> ```blocks3
> when this sprite clicked
> +start sound (Tennis Hit v)
> change [pizzas v] by (1)
> ```

> [!TASK]
>
> Make the sprite bounce a little when clicked.
>
> ```blocks3
> when this sprite clicked
> start sound (Tennis Hit v)
> change [pizzas v] by (1)
> +change size by (10)
> +wait (0.05) seconds
> +change size by (-10)
> ```

> [!TASK]
>
> Start a new script. On the green flag, set the sprite to
> `not draggable`{:class="block3sensing"} so the player clicks it instead of
> accidentally dragging it around the stage.
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> ```

> [!TASK]
>
> Add the win to the same script. It waits until the score is high enough, then
> celebrates.
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> +wait until <(pizzas) > (10000)>
> +start sound (Win v)
> +say [You Win!] for (2) seconds
> +stop [all v]
> ```

> [!TASK]
>
> Click the `Stage`{:class="block3looks"} and reset the score on the green flag.
>
> ![Selecting the Stage, to the right of the sprite list.](images/select-stage.png)
>
> ```blocks3
> when green flag clicked
> set [pizzas v] to (0)
> ```

Click the green flag. Your score starts at 0 and climbs each click.
