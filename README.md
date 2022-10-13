# 4-Player ELO Simulation

### This simulation takes in 2 parameters: `# of competitors` & `# of rounds`

#### I wanted to create a game that allows a user to pick their favorite choice out of four options. By picking their favorite, the winning compitor should go up in rank, while the losing compitors propotionately decrease in rank.

## ELO Algorithm

### I based this 4-player ELO off of the standard 2-player ELO Algorithm used on most chess websites:

![2p ELO](images/2p-ELO.png) <img src="images/2p-Rating.png" alt="2P New Rating" width="300"/>
##### E<sub>a</sub> = probability of `player a` winning
##### R<sub>a</sub> = Rating of `player a`; R<sub>b</sub> = Rating of `player b`
##### R<sub>A</sub> = Rating before; R<sup>'</sup><sub>A</sub> = Rating After
##### S<sub>A</sub> = `1` if player is winner; S<sub>A</sub> = `0` if player is loser

### The resulting 4-player version of this alogirthm is as follows:

### E<sub>a1</sub> = (1/(1+10<sup>(r<sub>2</sub>-r<sub>1</sub>)/400</sup>) + 1/(1+10<sup>(r<sub>3</sub>-r<sub>1</sub>)/400</sup>) + 1/(1+10<sup>(r<sub>4</sub>-r<sub>1</sub>)/400</sup>))/6
### E<sub>a2</sub> = (1/(1+10<sup>(r<sub>1</sub>-r<sub>2</sub>)/400</sup>) + 1/(1+10<sup>(r<sub>3</sub>-r<sub>2</sub>)/400</sup>) + 1/(1+10<sup>(r<sub>4</sub>-r<sub>2</sub>)/400</sup>))/6
### E<sub>a3</sub> = (1/(1+10<sup>(r<sub>1</sub>-r<sub>3</sub>)/400</sup>) + 1/(1+10<sup>(r<sub>2</sub>-r<sub>3</sub>)/400</sup>) + 1/(1+10<sup>r<sub>4</sub>-r<sub>3</sub>)/400</sup>))/6
### E<sub>a4</sub> = (1/(1+10<sup>(r<sub>1</sub>-r<sub>4</sub>)/400</sup>) + 1/(1+10<sup>(r<sub>2</sub>-r<sub>4</sub>)/400</sup>) + 1/(1+10<sup>(r<sub>3</sub>-r<sub>4</sub>)/400</sup>))/6

#### R<sup>'</sup><sub>A1</sub> = round(R<sub>A1</sub> + k(S<sub>A</sub> - E<sub>a1</sub>))
#### R<sup>'</sup><sub>A2</sub> = round(R<sub>A2</sub> + k(S<sub>A</sub> - E<sub>a2</sub>))
#### R<sup>'</sup><sub>A3</sub> = round(R<sub>A3</sub> + k(S<sub>A</sub> - E<sub>a3</sub>)) 
#### R<sup>'</sup><sub>A4</sub> = round(R<sub>A4</sub> + k(S<sub>A</sub> - E<sub>a4</sub>))

## Instructions

> 1. Clone Repo: `git clone git@github.com:P-Carth/Multiplayer-ELO-Simulation.git`
>
> 2. Open `ELO_Simulation.ipynb` in Jupyter Lab
>
> 3. Run the first 4 code blocks
>
> 4. The 5th code block begins the simulation, where it will ask you to input `# of rounds` and `# of competitors`
>
> 5. Finally, run the last code block to view the simulation's analysis

## Results & Discussion

![Ranking Distribution](images/histogram.png)

> While I was successful in creating a normally distributed 4-Player ELO System, it does seem that there is a consistent skew to the right. Fortunately, for my purposes this is not an issue.

> This algorithm can be applied to a number of scenarios to compare competitors in an adjusted and fair manner. For example, I applied this algorithm to an NFT game that I made with Flask that allows users to vote on their favorite NFT (<i>shown below<i>).

![NFT Game](images/nft-game.png)
