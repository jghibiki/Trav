# Trav

A few automation scripts to make Traveler RPG game play a little more streamlined. The scripts should try to remain reletively transparent where scores are coming from so that they can be validated manually, step-by-step.

**Note:** All scripts have a help section that is visible by appending ```--help``` to the end of any command. e.g. ```trav --help``` will list trav scripts ```trav passengers --help``` will show help for the passengers script.


## Available Scripts

### Calculate Availiable Passengers


#### Example #1 

Notice how in this case steward level is set to 0, this means that the player can take either 2 high passengers or 5 middle passengers. After rolls for passenger availiability, we see that there are 3 high passengers and 11 medium passengers. Instead of dumbly taking as many high passengers as possible ( in this case two, for a total profit of 1200CR ), the script smartly calculates the most lucrative combination. In this case the most profitable option is to take 5 medium passengers
for a total profit of  1500CR.

**Command:**
```
./trav passengers --current "Agricultural" --destination "Water world, Rich" --dm 4 --staterooms 10 --low-berths 20 --steward-level 0
```

**Output:**
```
Streetwise/Carouse Check (2d6 + 4):
|-> Roll:14
|-> Calculated Effect: 6

World Modifiers:
|-> Current:
| |-> Agricultural: 0
| |-> TOTAL: 0
|
|-> Destination:
| |-> Water world: 0
| |-> Rich: 2
| |-> TOTAL: 2

Total Modifiers:
|-> Effect Modifier (half of effect): 3
|-> Current World Modifier: 0
|-> Destination World Modifier: 2
|-> TOTAL: 2

Availiable Passengers:
|-> High: 3
|-> Medium: 11
|-> Low Berth: 6

Passenger Optimization:
|-> High Passengers: 0 * 6000 = 0 CR
|-> Medium Passengers: 5 * 3000 = 15000 CR
|-> Low Berth Passengers: 6 * 1000 = 6000 CR
|-> TOTAL INCOME: 21000 CR
```

**Command:**
```
./trav passengers --current "Agricultural" --destination "Water world, Rich" --dm 2 --staterooms 10 --low-berths 20 --steward-level 1
```

**Output:**
```
Streetwise/Carouse Check (2d6 + 2):
|-> Roll:14
|-> Calculated Effect: 6

World Modifiers:
|-> Current:
| |-> Agricultural: 0
| |-> TOTAL: 0
|
|-> Destination:
| |-> Water world: 0
| |-> Rich: 2
| |-> TOTAL: 2

Total Modifiers:
|-> Effect Modifier (half of effect): 3
|-> Current World Modifier: 0
|-> Destination World Modifier: 2
|-> TOTAL: 2

Availiable Passengers:
|-> High: 2
|-> Medium: 5
|-> Low Berth: 8

Passenger Optimization:
|-> High Passengers: 2 * 6000 = 12000 CR
|-> Medium Passengers: 5 * 3000 = 15000 CR
|-> Low Berth Passengers: 8 * 1000 = 8000 CR
|-> TOTAL INCOME: 35000 CR
```
