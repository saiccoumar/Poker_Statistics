# Poker Statistics ♡ ♣ ♢ ♠
<p align="center">
 <img size="100%" src="https://github.com/saiccoumar/Poker/assets/55699636/e0613b16-97a4-43d3-970c-a5d1f1a20f35">
</p>

by Sai Coumar

# Introduction
Welcome to my initial statistical investigation into Poker theory! This repository is being separated from and ported over Poker_rl which will be continued as a testbed for poker reinforcement learning. 


## Poker Simulations
My first iteration of this project was with poker_simulations.py. You can run this for yourself using the command:
```
python poker_simulations.py
```
poker_simulations.py uses a rudimentary ruleset of the game to generate simulated data of poker. I created the class TexasHoldEm, which has a deck, community cards, and the hands of each players. It also has the functionality to deal community cards and hole cards. This class has many methods, many of which are for recording data and managing the game, but there are two in particular to take note of.

***play_round()*** simulates a single round of poker. It resets the cards in the deck, shuffles them, and then deals 2 to each player and 5 onto the community cards; This effectively skips to the showdown round. 

***determine_winner()***, and it's helper method ***rank_hand()***, is the bread and butter of this program. determine_winner() evaluates the 2 cards each player + 5 community cards and then sorts them by their rank. It then returns the index of the hand that won. ***rank_hand()*** takes 7 cards, and then returns the rank of the best combination of 5 cards that can be made with those 5 cards. 

In poker there are 10 ranks, with the Royal flush being the highest (rank 10) and the high card being the lowest (rank 1). It also returns the value of the highest card, because if two hands have the same rank, the player with the higher card value wins. rank_hand() was tested extensively in tests.py, and I recommend checking the logic yourself if you're interested.
<p align="center">
  <img width="60%" height="auto" src="https://github.com/saiccoumar/Poker/assets/55699636/c83703ac-860c-4b66-bef3-3676b0e92ac9">
</p>
<p align="center">
  <em> https://www.poker.org </em>
 <em> I ranked mine with 1 as the lowest and 10 as the highest. This graphic reverses that.</em>
</p>
Also note that this is not the most efficient implementation of rank_hand(). In my research I found that bit-wise evaluations of hands were far more efficient for large scale poker applications on servers. 
   <br />

In the code, you can vary num_rounds and num_players to get the simulated data you desire.  

There is also a function, ***draw_probabilities()*** which calculates the probabilities of having a hand of a rank with 2 random cards (an opponents cards) given the community cards available. This was made in advance because such probabilities will be more useful when implementing the AI agents.. 
![evaluator_test](https://github.com/saiccoumar/Poker/assets/55699636/f3cd1263-12ea-4cc0-8f55-86751488ad87)

Win and loss counts are recorded as CSVs in the subdirectories `wins` and `losses`. Various frequency data of poker hands is collected and stored in the subdirectory `frequencies`.

## Poker Analysis (ipynb)
poker_analyis.ipynb contains all my statistical analyses of the data collected from poker_simulations.py. I generated various plots and calculated metrics regarding poker statistics.

:warning: UNDER CONSTRUCTION :warning:

#### Gallery:
<p align="center">
 <img size="100%" src="https://github.com/saiccoumar/Poker/assets/55699636/4a3591a7-10c3-4364-a16d-face2a3cff61">
</p>
<p align="center">
 <img size="100%" src="https://github.com/saiccoumar/Poker/assets/55699636/894bf6b3-a5e5-45fc-b738-bb1c19afbf5a">
</p>
<p align="center">
 <img size="100%" src="https://github.com/saiccoumar/Poker/assets/55699636/1f151d6c-b726-4de7-899f-16683ad42512">
</p>

