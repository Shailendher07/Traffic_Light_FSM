# Traffic_Light_FSM
This project simulates a realistic traffic signal control system using a Finite State Machine (FSM), written in Verilog HDL. It models the behavior of a typical 4-way road intersection with enhanced traffic flow rules, emergency responsiveness, and pedestrian safety logic.

The controller cycles through 13 defined states, covering:
Normal operation: green and yellow phases for North, East, South, and West
Emergency scenarios: asynchronous override when a signal (like emergency_north) is triggered

Each phase is time-controlled:
Green stays ON for 10s
Yellow follows for 5s

In this traffic light controller, signals change according to the active FSM state to coordinate traffic flow safely and efficiently. For example, during the north_green state, north_vehicles is set to 10 (allowing straight and right turns), while the other directions (south_vehicles, east_vehicles, west_vehicles) are limited to 01 (free left turns only). Similarly, during east_green, east_vehicles is set to 10 while all others remain in limited movement. In emergency states (e.g., emergency_west_green), the relevant direction (like west_vehicles) is set to 11, allowing movement in all directions while other directions are fully stopped. Four dedicated pedestrian control signals are used to manage safe crossing paths across a 4-way intersection. These are: pesdestrains_Nleft_to_S, pesdestrains_Sleft_to_N, pesdestrains_Eleft_to_W, and pesdestrains_Wleft_to_E
pesdestrains_Nleft_to_S enables crossing from the left side of the North road to the South side, and is active during the north_green and north_yellow states.
pesdestrains_Sleft_to_N controls the path from the left side of the South road to the North, becoming active during the south_green and south_yellow states.
pesdestrains_Eleft_to_W allows pedestrians to cross from the left side of East road to West, while
pesdestrains_Wleft_to_E manages the left of West to East crossing. These last two are activated during east_green/east_yellow and west_green/west_yellow respectively.
