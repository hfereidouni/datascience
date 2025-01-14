# Part 4: Feature Engineering II

## Questions 1 to 4

**Features selected**:
`['game_time','period','x','y','shot_type','last_event_type',
    'x_coord_last_event', 'y_coord_last_event', 'Time_from_the_last_event',
    'Distance_from_the_last_event', 'Rebound', 'change_shot_angle', 'Speed',
    'shot_dist','angle_net', 'is_goal']`
    
### Question 1:
- **game_time**: The time (seconds) where this event happened in current game.
- **period**: The period that in which event happened in current game.
- **x**, **y**: The `x` and `y` coordinate of where this event happened in current game.
- **shot_type**: Type of shot of the this event.
- **shot_dist**: The distance of this event to the net of the attack rinkside.
- **angle_net**: The angle of this event to the net of the attack rinkside, calculated using `shot_dist`.

### Question 2:
- **last_event_type**: Type of event (play) of the previous event (of this event) in current game.
- **x_coord_last_event**, **y_coord_last_event**: The x and y coordinate of where the previous event happened in current game.
- **Time_from_the_last_event**: The time (seconds) where the previous event happened in current game.
- **Distance_from_the_last_event**: the distance between the coordinates of this event and the coordinates of the previous event.

### Question 3:
- **Rebound**: A boolean value of whether this event is a rebound (the previous event was also a shot) or not.
- **change_shot_angle**: The difference of angle of the shot of this event and that of the previous event, this is only a valid value if this event is a `rebound`.
- **Speed**: The average speed between the previous event and this event, calculated using `Distance_from_the_last_event` divided by `Time_from_the_last_event`.

### Other:
- **is_goal**: A binary Label that if this event is a goal: 1 if it's a goal otherwise 0.

### Overview of filtered Dataframe
![df](./images/part%204/dataframe.jpg)


## Question 5

**The filtered DataFrame artifact for the specified game (wpg_v_wsh_2017021065):**
[Comet.ml](https://www.comet.com/hfereidouni/ift6758/41a02783a9d54633a47fd78acfb9a900?experiment-tab=panels&showOutliers=true&smoothing=0&xAxis=step)
