## Make the clicker

Add something to click and a score that goes up when you click it.

> [!TASK]
>
> Delete the cat sprite. Add your own sprite with **Choose a Sprite** (library,
> **Upload**, or **Paint**). The pizza shop uses a pizza.

> [!TASK]
>
> Make a variable called `pizzas`{:class="block3variables"} and tick it so the
> player can see their score.

> [!TASK]
>
> Add this to your sprite so clicking it makes a pizza.
>
> ```blocks3
> when this sprite clicked
> start sound (Tennis Hit v)
> change [pizzas v] by (1)
> change size by (10)
> wait (0.05) seconds
> change size by (-10)
> ```

Click your sprite. The `pizzas`{:class="block3variables"} score goes up.

> [!TASK]
>
> Set the win threshold. Add this script so the player wins at `10000` pizzas.
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> wait until <(pizzas) > (10000)>
> start sound (Win v)
> say [You Win!] for (2) seconds
> stop [all v]
> ```

> [!TASK]
>
> Click the `Stage`{:class="block3looks"} and reset the score on the green flag.
>
> ```blocks3
> when green flag clicked
> set [pizzas v] to (0)
> ```

Click the green flag. Your score starts at 0 and climbs each click.
