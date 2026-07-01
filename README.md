# Callbreak Monte Carlo Simulation

An interactive Python simulation utilizing randomized probability modeling and Monte Carlo method to analyze player performance trends using real world card game data.

---

## 🎯 Objective
The goal of this project is to model and predict player performance in the card game Callbreak using a **Monte Carlo Simulation approach**. Instead of relying on short-term static averages, this project uses historical game data from 14 real games to simulate thousands of hypothetical rounds. This allows us to observe how random luck naturally neutralizes over time, revealing the true underlying efficiency of each player's playstyle.

---

## 📊 The Dataset & Player Archetypes
The simulation tracks 4 players with highly distinct playstyles based on a 14-game historical matrix:
* **Player P & V:** Conservative, low risk players who focus on consistent, smaller wins.
* **Player M & U:** Aggressive, high risk players who look for massive point hauls but carry a higher probability of getting their bids broken.

---

## 🛠️ Implementation & Logic

The project breaks down the historical data using custom analytical metrics to drive a randomized simulation loop:

1. **`avg_increment(player)`**: Computes the average point value a player gains when they successfully make a bid.
2. **`avg_decrement(player)`**: Computes both the average points lost and the total frequency count of getting broken.
3. **`cont(player, m)`**: The simulation core. It calculates the dynamic historical probability of getting broken (`loss_chance = c / 14`). For every simulated game:
   * If a random roll falls within the loss chance, the player suffers their historical average penalty.
   * If they win, the engine randomly samples an actual positive scoring round from their past data to build out their cumulative trajectory.

---

## 📉 Experimental Insight: The Law of Large Numbers

The simulation highlights a key contrast between short-term noise and long-term trends:

1. **Short Term Chaos:** At low iterations, **Luck is the dominant factor**. The short-term starting scores create an initial offset. If you change the number of simulations slightly, temporary streaks wildly distort the trends and rankings constantly flip.
2. **Long Term Convergence:** When scaled up to a massive number of rounds (e.g., 10,000 games), individual instances of "good luck" and "bad luck" perfectly balance out to zero. The random noise hits $0$ and the lines smooth out completely. 

---
## 🔗 Live View
[Link To Notebook](https://nbviewer.org/github/veeedant/callbreak-game-monte-carlo-sim/blob/main/callbreak_simulation.ipynb)
