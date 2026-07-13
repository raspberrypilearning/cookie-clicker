## Add a second helper

One helper is good; two is better. In this step you'll add a second, more powerful
helper that makes more pizzas per second than the first. The pizza shop hires
grannies, because grannies are pizza pros.

> [!TASK]
>
> Add another helper sprite. The pizza shop uses a granny, but pick whatever fits
> your game.

> [!TASK]
>
> Copy your chef's two scripts onto the new sprite: drag each script from the code
> area and drop it onto the new sprite in the sprite list. This copies them so you
> don't have to rebuild every block.

> [!TASK]
>
> Make two new variables for this helper:
>
> - `grannies`{:class="block3variables"} — how many you've hired.
> - `granny price`{:class="block3variables"} — how many pizzas the next one costs.
>
> Then, in the copied scripts, swap the chef variables for the granny ones and pick
> a different sound. Your buy script should look like this:
>
> ```blocks3
> when this sprite clicked
> start sound (Collect v)
> change [pizzas v] by ((0) - (granny price))
> change [grannies v] by (1)
> set [granny price v] to (round ((granny price) * (1.15)))
> ```
>
> And your appear script like this:
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> forever
> if <(pizzas) > ((granny price) - (1))> then
> show
> else
> hide
> end
> broadcast (update v)
> end
> ```

> [!TASK]
>
> Now make grannies actually worth it. On the `Stage`{:class="block3looks"}, update
> the `update pizzas per second`{:class="block3custom"} definition so each granny
> adds `5` pizzas a second on top of what your chefs make.
>
> ```blocks3
> define update pizzas per second
> +set [pizzas per second v] to (((chefs) * (1)) + ((grannies) * (5)))
> ```

> [!TASK]
>
> Then give the two new variables their starting values in the Stage's green flag
> script. A granny starts at `100` pizzas — pricier than a chef, because she works
> harder.
>
> ```blocks3
> when green flag clicked
> set [pizzas v] to (0)
> set [pizzas per click v] to (1)
> set [chefs v] to (0)
> set [chef price v] to (15)
> +set [grannies v] to (0)
> +set [granny price v] to (100)
> update pizzas per second
> forever
> wait (1) seconds
> change [pizzas v] by (pizzas per second)
> end
> ```

Click the green flag and play for real. Buy chefs, then save for a granny and watch
your pizzas-per-second jump. You now have a full endless clicker: clicks, upgrades,
and helpers all working together.

> [!SAVE]
