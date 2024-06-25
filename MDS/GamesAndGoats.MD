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

### Code

```python
doors = [0,1,2] #rg, bg, car
W = 0 # Number of Wins
L = 0 # Number of Loses
S = 0 # Number of Switches
P1 = 0.14 #Probability of not switching on goat 1
P2 = 0.05 #Probability of not swtiching for goat 2
PT = P1 + P2 #Sum of the two probabilties
Sp = (PT-2.)/(PT-3.) # Predicted Switching Power
Cw = 2./3 - PT/3 #Predited chances of winning

fig, ax = plt.subplots() #Begin Plot
def update(i):
    global W
    global L
    global S
    ax.clear()
    ax.cla()
    ax.set_ylim(0,1)
    random.shuffle(doors)
    ax.hlines(Cw, -0.5, 0.5, colors='gold', linestyles='dashed')  # Add horizontal line
    ax.hlines(1-Cw, 0.5, 1.5, colors='red', linestyles='dashed')  # Add horizontal line
    ax.hlines(Sp, 1.5, 2.5, colors='powderblue', linestyles='dashed')  # Add horizontal line
    for _ in range(10):
        gorc = random.choice(doors) #goat or car
        if gorc == 0: #goat 1
            if random.uniform(0, 1) <=P1:
                L+=1
            else:
                W+=1
                S+=1
        elif gorc == 1: #goat 2
            if random.uniform(0, 1) <=P2:
                L+=1
            else:
                W+=1
                S+=1
        else: #car
            L+=1
            S+=1
    
    ax.bar(x = ['Wins', 'Loses', 'S-Power'], height = [W/(W+L),L/(W+L), W/(0.000001+S)], color=['gold', 'red', 'powderblue'])
    
# Create the animation
ani = FuncAnimation(fig, update, frames=range(5000), repeat=False, blit=False)

# Save the animation as a GIF
ani.save('DoubleGoat.gif', writer=PillowWriter(fps=24))
plt.show()

PT = np.linspace(0,2, 1000)
Cw = 2./3-1/3*(PT)
Sp = (PT-2)/(PT-3)

plt.plot(PT, Cw, label=r'$C_w$')
plt.plot(PT, Sp, label=r'$S_p$')
plt.axhline(0.5, c='k', ls=':')
plt.axvline(1.0, c='k', ls=':')
plt.xlabel(r"$P_T$")
plt.legend()

plt.savefig('Goat_bow.png', bbox_inches='tight')
plt.show()
```

## Greedy Piggies

## SIRD Modelling
