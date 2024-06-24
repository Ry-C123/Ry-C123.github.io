# Games and Goats

One thing I liked about outreach is that I could often demonstrate the intersection of different subjects. In this case, maths and coding! Mathematical modelling is one of those topics that can be difficult to demonstrate in an engaging way as the barrier to entry is steep. Here are a few demonstrations I used to do :

## Monty Hall +

The Monty Hall Problem is a well known maths puzzle. The concept being, there are 3 doors behind two of the doors are goats, behind the remaining door is a car. Your job is to pick one of the doors, then Monty will remove one of the remaining doors containing a goat. You then have the option to switch the door. The surprising outcome is that you will win two thirds of the time if you choose to switch. This result can be explained easily if you look at how the all the possible outcomes at once.

<img src="/images/GanGs/wwl.PNG?raw=true"/>

We can run a simulation to show this:

<img src="/images/GanGs/REGULAR.gif?raw=true"/>

Thing is, that's easy. What happens if you aren't given the option to switch if you pick one of the goats (the blue goat). Now we can only win a third of the time; what's worse, it doesn't matter if we chose to switch or not. Our switching power is 50%. The blue goat makes the game a lot harder to win.

<img src="/images/GanGs/lwl.PNG?raw=true"/>

Another simulation:

<img src="/images/GanGs/BlueGoat.gif?raw=true"/>

A next step to make things more exciting is to make it so the blue goat has a *chance* of not switching. We call this chance P. 
This means your chance of winning becomes the sum of winning by picking each door.

<img src="/images/GanGs/bwp.PNG?raw=true"/>
<img src="/images/GanGs/Cw.PNG?raw=true"/>

<img src="/images/GanGs/ppl.png?raw=true"/>

<img src="/images/GanGs/DoubleGoat.gif?raw=true"/>


$$
Strategy =
\\begin{cases}
\\text{Switch} & \\quad \\text{when $P_T < 1$}\\\\
\\text{Coin Toss} & \\quad \\text{when $P_T = 1$}\\\\
\\text{Stick} & \\quad \\text{when $P_T> 1$}
\\end{cases}
$$




## Greedy Piggies

## SIRD Modelling
