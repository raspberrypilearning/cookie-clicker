## Make the clicker

In this step, you'll add something to click and a counter that goes up every time
you click it. This is the heart of the game.

> [!TASK]
>
> Add a sprite for the thing you want to make. In the pizza shop it's a pizza, but
> it could be a cookie, a car, a coin, or anything you like.
>
> Hover over **Choose a Sprite** in the bottom-right and either pick one from the
> library, **Upload** your own picture, or click **Paint** to draw one.
>
> Delete the cat sprite if you don't need it.

You should now have one sprite in the middle of the stage.

> [!TASK]
>
> Make two variables. Click **Make a Variable** in the
> `Variables`{:class="block3variables"} palette.
>
> - `pizzas`{:class="block3variables"} counts how many you've made so far.
> - `pizzas per click`{:class="block3variables"} is how many you make with a
>   single click.
>
> Use whatever names fit your game (`cookies`, `coins`…), but keep them
> consistent.
>
> Tick the checkbox next to `pizzas`{:class="block3variables"} so the player can
> watch their score. You can show `pizzas per click`{:class="block3variables"}
> too, or untick it to keep it hidden.

> [!TASK]
>
> Click your pizza sprite to select it, then add this script so a click makes
> pizzas. The `start sound`{:class="block3sound"} and the size wobble give the
> player feedback that the click worked.
>
> ```blocks3
> when this sprite clicked
> start sound (Tennis Hit v)
> change [pizzas v] by (pizzas per click)
> change size by (10)
> wait (0.05) seconds
> change size by (-10)
> ```
>
> Pick your own short sound: click the **Sounds** tab, then the speaker icon, and
> choose something snappy from the **Effects** or other categories.

Click the green flag, then click your pizza. The `pizzas`{:class="block3variables"}
counter goes up and the pizza gives a little bounce each time.

> [!TASK]
>
> Now add a way to win. Add this second script to your pizza sprite. It stops the
> pizza being dragged around, then waits until the player has made enough pizzas
> before celebrating.
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> wait until <(pizzas) > (10000)>
> start sound (Win v)
> say [You Win!] for (2) seconds
> stop [all v]
> ```
>
> `10000` is the pizza shop's target. Pick a win number that feels right for your
> game.

> [!TASK]
>
> Finally, click the `Stage`{:class="block3looks"} (bottom-right, next to the
> sprites) and add this script so the game starts fresh every time.
>
> ```blocks3
> when green flag clicked
> set [pizzas v] to (0)
> set [pizzas per click v] to (1)
> ```

> [!TIP]
>
> Setting `pizzas per click`{:class="block3variables"} to `1` here matters: a brand
> new variable starts at `0`, and clicking would add nothing. Setting it to `1`
> means every click makes one pizza to begin with.

Click the green flag and click away. Your counter climbs by one each time, and if
you're very patient you'll see the win message.
