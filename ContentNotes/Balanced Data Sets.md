For a balanced dataset, its smart to use a combination of continuous and random frames. 

## *Continuous Frames*

*Purpose*: Allows the model to learn movement patterns and sequential actions over time. Like a player dribbling or passing. One frame build on the previous frame

*How to Use*: Label small sequences around key actions
* Dribbling or passing
* Defensive actions, how players respond to each other
* goalie saving
* a Goal
* Corner kicks

**Benefits**: This helps the model understand transitions between different actions, which improves its ability to recognize behaviors that change over time.

## *Random, Non-Sequential Frames*

*Purpose*: It adds variety and reduces bias by including a range of positions field locations, the player activities. Its give a global view and understanding. 

*How to use*: Choose frames accross the gae that show different scenarios, different player formations and player activities. 
* Players on different zones of the field
* Game situations like, freekicks, corner kicks counter atacks. 

**Benefits**: This diversity helps the model generalize better, making it less reliant on sequential data and more robust across different game contexts.

[[Data sets]]