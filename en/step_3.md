## Add the first equipment

Add equipment the player can unlock to make every click worth more.

> [!TASK]
>
> Make a variable called `pizzas per click`{:class="block3variables"}. This is how much one click adds to the demo project's score.
>
> If your score variable is not `pizzas`{:class="block3variables"}, give this variable a matching name, such as `coins per click` or `goals per click`.

> [!TIP]
>
> All the changing information a game remembers, like scores, prices, and upgrades, is called the **game state**.

> [!TASK]
>
> Click the `Stage`{:class="block3looks"} and set `pizzas per click`{:class="block3variables"} to `1` on the green flag, so a click always adds at least one.
>
> ![Selecting the Stage, to the right of the sprite list.](images/select-stage.png)
>
> ```blocks3
> when green flag clicked
> set [pizzas v] to (0)
> +set [pizzas per click v] to (1)
> ```

> [!TASK]
>
> On your main clicker sprite, make each click use the variable instead of a fixed `1`.
>
> <p align="center"><img src="images/pizza.png" alt="Pizza sprite icon." width="96" height="96" style="object-fit: contain;"></p>
>
> ```blocks3
> when this sprite clicked
> start sound (Tennis Hit v)
> +change [pizzas v] by (pizzas per click)
> change size by (10)
> wait (0.05) seconds
> change size by (-10)
> ```

Nothing changes yet, because `pizzas per click`{:class="block3variables"} is still `1`. The equipment will raise it.

> [!TASK]
>
> Add your first piece of equipment as a new sprite. Choose something that looks like it would improve each click, such as a tool, machine, power-up, or badge. The demo project uses a cutter.
>
> Use your own equipment, or save [the cutter sprite](images/cutter.png) and import it with **Upload**.
>
> ![The demo project's cutter.](images/cutter.png)

> [!TASK]
>
> Select the equipment sprite and use the **Size** box below the Stage to make it fit. The demo project's cutter is `30`% size.
>
> Drag it near the bottom of the Stage, leaving room for two more equipment sprites beside it.

> [!TASK]
>
> In the **Costumes** tab, right-click the equipment costume and choose **duplicate**. Keep the plain costume first and the copied costume second.
>
> ![Right-clicking a costume to duplicate it in the Costumes tab.](images/duplicate-costume.png)

> [!TASK]
>
> Change the second costume so it clearly shows the equipment has been bought. The demo project adds a green tick.
>
> ![The cutter costume with a green tick added.](images/cutter2.png)

> [!TASK]
>
> Add the `Alert`{:class="block3sound"} sound to your equipment sprite.

> [!TASK]
>
> Set up the equipment on the green flag: make it not draggable, switch to the plain costume, and hide it.
>
> <p align="center"><img src="images/cutter.png" alt="Cutter sprite icon." width="96" height="96" style="object-fit: contain;"></p>
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> switch costume to (cutter v)
> hide
> ```

> [!TASK]
>
> Make the equipment appear only once the player can afford it. The sound and speech bubble tell the player what has just appeared.
>
> The cutter costs `25` of the score variable, so it appears when the player has more than `24`. Use bigger numbers to make later equipment more expensive.
>
> ```blocks3
> when green flag clicked
> set drag mode [not draggable v]
> switch costume to (cutter v)
> hide
> +wait until <(pizzas) > (24)>
> +show
> +start sound (Alert v)
> +say [New equipment unlocked!] for (2) seconds
> ```

> [!TIP]
>
> An **unlock condition** is a rule that makes something available only after the player has done enough.

> [!TASK]
>
> Add the `Tada`{:class="block3sound"} sound to your equipment sprite.

> [!TASK]
>
> Make it buyable. Clicking it spends `25` of the score variable, upgrades the player's clicks, and switches to the "bought" costume.
>
> The `costume number = 1` check means only the plain costume can be bought, so the player cannot buy the same upgrade twice.
>
> <p align="center"><img src="images/cutter.png" alt="Cutter sprite icon." width="96" height="96" style="object-fit: contain;"></p>
>
> ```blocks3
> when this sprite clicked
> if <<(costume [number v]) = (1)> and <(pizzas) > (24)>> then
> start sound (Tada v)
> change [pizzas v] by (-25)
> set [pizzas per click v] to (2)
> next costume
> end
> ```

Click until the score reaches 25. The cutter appears; click it to spend 25 and make every click worth 2.

> [!TIP]
>
> Game developers often build and test one working **prototype** first. Fixing the cutter before copying its scripts makes problems easier to find.
