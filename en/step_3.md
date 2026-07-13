## Add equipment

Clicking one pizza at a time is slow. In this step, you'll add **equipment** the
player can unlock to make every click worth more. In the pizza shop that's a pizza
cutter, a rolling pin, and an oven, but you can pick whatever suits your game.

Each piece of equipment changes `pizzas per click`{:class="block3variables"}, appears
only once the player has enough pizzas, and can be bought once.

> [!TASK]
>
> Add your first piece of equipment as a new sprite (**Choose a Sprite** →
> library, **Upload**, or **Paint**). The pizza shop uses a `cutter`.
>
> Then give it a second costume that shows it's been bought. Click the **Costumes**
> tab, right-click your costume and choose **duplicate**, then change the copy: the
> pizza shop adds a big green tick. You could add a cross, grey it out, or recolour
> it. Make sure the plain costume is first and the "bought" one is second.

> [!TASK]
>
> Add this script so the cutter only appears once the player can afford it. The
> `start sound`{:class="block3sound"} gives an "it's ready!" nudge.
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> switch costume to (cutter v)
> forever
> if <(pizzas) > (25)> then
> start sound (Alert v)
> show
> else
> hide
> end
> end
> ```
>
> `25` is the pizza shop's unlock number. Pick your own, and switch to your first
> costume's name instead of `cutter`.

> [!TASK]
>
> Now add the buy script. When the player clicks the cutter it upgrades their
> clicks, switches to the "bought" costume, and shuts itself off so it can't be
> bought again.
>
> ```blocks3
> when this sprite clicked
> start sound (Tada v)
> set [pizzas per click v] to (2)
> next costume
> stop [other scripts in sprite v]
> stop [this script v]
> ```

> [!TIP]
>
> The unlock number is a threshold, not a cost: the cutter appears when the player
> has more than `25` pizzas, and buying it doesn't spend them. The helpers you add
> later *will* cost pizzas.

Click the green flag and click until you pass 25 pizzas. The cutter appears; click
it and every click is now worth 2 pizzas.

> [!TASK]
>
> Add two more pieces of equipment the same way. The quickest route: for each new
> sprite, drag your two cutter scripts from the code area onto the new sprite in the
> sprite list to copy them, then change the numbers.
>
> Use bigger unlock numbers and bigger upgrades each time so equipment stays worth
> saving for. The pizza shop's rolling pin appears above `499` pizzas and sets
> `pizzas per click`{:class="block3variables"} to `6`:
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> switch costume to (rolling_pin v)
> forever
> if <(pizzas) > (499)> then
> start sound (Alert v)
> show
> else
> hide
> end
> end
> ```
>
> ```blocks3
> when this sprite clicked
> start sound (Tada v)
> set [pizzas per click v] to (6)
> next costume
> stop [other scripts in sprite v]
> stop [this script v]
> ```
>
> Then add a third piece the same way — the pizza shop's oven appears above `3000`
> pizzas and sets `pizzas per click`{:class="block3variables"} to `24`. Remember to
> switch each sprite to its own first costume near the top of its "appear" script.

> [!TASK]
>
> Now make winning depend on buying everything. Click your pizza sprite and update
> the `wait until`{:class="block3control"} in its win script so the player needs a
> high score **and** all the upgrades (which lands
> `pizzas per click`{:class="block3variables"} on `24`).
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> +wait until <<(pizzas) > (10000)> and <(pizzas per click) = (24)>>
> start sound (Win v)
> say [You Win!] for (2) seconds
> stop [all v]
> ```
>
> If you chose different upgrade values, use your own final
> `pizzas per click`{:class="block3variables"} number here.

Click the green flag. Buy all three pieces of equipment and keep clicking — now the
win message only appears once you've kitted out your whole shop.
