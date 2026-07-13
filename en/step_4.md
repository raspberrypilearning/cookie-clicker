## Add auto-clickers

Real clicker games keep making things even when you stop clicking. In this step
you'll add a **helper** that makes pizzas for you every second. The pizza shop
hires chefs, but yours could be robots, workers, or magic ovens.

> [!TASK]
>
> Add a helper sprite (**Choose a Sprite** → library, **Upload**, or **Paint**).
> The pizza shop uses a robot chef.

> [!TASK]
>
> Make three new variables:
>
> - `chefs`{:class="block3variables"} — how many helpers you've hired.
> - `chef price`{:class="block3variables"} — how many pizzas the next helper costs.
>   This one climbs each time you buy, so helpers get pricier.
> - `pizzas per second`{:class="block3variables"} — how many pizzas your helpers make
>   each second.
>
> Tick `chefs`{:class="block3variables"} and
> `pizzas per second`{:class="block3variables"} so the player can watch them; you
> can hide `chef price`{:class="block3variables"} or show it, your choice.

> [!TASK]
>
> Add this buy script to your helper. It spends pizzas, hires one helper, then
> raises the price for next time.
>
> ```blocks3
> when this sprite clicked
> start sound (Clang v)
> change [pizzas v] by ((0) - (chef price))
> change [chefs v] by (1)
> set [chef price v] to (round ((chef price) * (1.15)))
> ```

> [!INFO]
>
> Multiplying the price by `1.15` and rounding it makes each helper cost about 15%
> more than the last. That steady climb is what stops the player buying everything
> at once, and it's the trick at the heart of every endless clicker.

> [!TASK]
>
> Add a second script so the helper only shows when the player can afford it, and
> tells the rest of the game to recount the pizzas-per-second.
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> forever
> if <(pizzas) > ((chef price) - (1))> then
> show
> else
> hide
> end
> broadcast (update v)
> end
> ```

> [!TASK]
>
> Now teach the `Stage`{:class="block3looks"} to run the game's clock. First make a
> custom block: in the `My Blocks`{:class="block3custom"} palette click **Make a
> Block**, name it `update pizzas per second`, and build its definition.
>
> ```blocks3
> define update pizzas per second
> set [pizzas per second v] to ((chefs) * (1))
> ```
>
> Then add a script so any helper can ask for a recount.
>
> ```blocks3
> when I receive (update v)
> update pizzas per second
> ```

> [!TASK]
>
> Finally, update the Stage's green flag script. It sets the new variables to their
> starting values, works out the rate once, then adds your pizzas-per-second every
> second, forever.
>
> ```blocks3
> when green flag clicked
> set [pizzas v] to (0)
> set [pizzas per click v] to (1)
> +set [chefs v] to (0)
> +set [chef price v] to (15)
> +update pizzas per second
> +forever
> wait (1) seconds
> change [pizzas v] by (pizzas per second)
> end
> ```

Click the green flag and click until you can afford a chef. Buy one, then stop
clicking: your `pizzas`{:class="block3variables"} keep rising on their own.
