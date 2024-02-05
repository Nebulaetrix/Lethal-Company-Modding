`weatherType`:
- [[Rainy| 1 - Rainy]]
- [[Stormy|2 - Stormy]]
- [[Foggy|3 - Foggy]]
- [[Flooded| 4- Flooded]]
- [[Eclipsed|5 - Eclipse]]

`weatherVariables` are values that vary depending on each moon, they are used to control the amount of entities spawned at the start of a game
```
- weatherType: 5
    weatherVariable: 4
    weatherVariable2: 0
```
`weatherType` references which type of weather it is, in this case, it's eclipsed
`weatherVariable` is the number of indoor enemies to spawn
`weatherVariable2` is the number of outdoor enemies to spawn 
