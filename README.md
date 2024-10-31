# 4-Way Traffic Light Controller

## Description
This project implements a 4-way traffic light controller using Verilog. It simulates traffic lights for North-South (NS) and East-West (EW) directions, utilizing a state machine to manage light changes based on predefined timing for each state.

## Features
- **State Management**: The controller cycles through four states: 
  - NS_GREEN
  - NS_YELLOW
  - EW_GREEN
  - EW_YELLOW
- **Timing Control**: Green lights remain active for a specified duration followed by a yellow light, facilitating a smooth transition between directions.
- **Modular Design**: The project follows a structural approach with distinct modules for timer, state machine, and output control.

## Project Structure
```
/4-way-traffic-light-controller
├── src
│   ├── traffic_light_controller.v      # Top-level module
│   ├── timer.v                          # Timer module
│   ├── state_machine.v                  # State machine module
│   └── output_control.v                 # Output control module
├── tb
│   └── traffic_light_controller_tb.v     # Testbench module
└── README.md                            # Project documentation
```

## Modules

### Timer Module
Controls the timing for each state and generates a time-up signal when the target count is reached.
```verilog
module timer (
    input wire clk,
    input wire reset,
    input wire [6:0] target_count, // Input for target count
    output reg time_up             // Time-up signal
);
// Timer code here
endmodule
```

### State Machine Module
Manages state transitions based on timer signals.
```verilog
module state_machine (
    input wire clk,
    input wire reset,
    input wire time_up,
    output reg [1:0] state
);
// State machine code here
endmodule
```

### Output Control Module
Sets the light outputs according to the current state.
```verilog
module output_control (
    input wire [1:0] state,
    output reg [2:0] ns_light,
    output reg [2:0] ew_light
);
// Output control code here
endmodule
```

### Top-Level Traffic Light Controller Module
Combines all modules into a single traffic light controller.
```verilog
module traffic_light_controller (
    input wire clk,
    input wire reset,
    output wire [2:0] ns_light,
    output wire [2:0] ew_light
);
// Top-level module code here
endmodule
```

## Testbench
The project includes a testbench that verifies the functionality of the traffic light controller by monitoring outputs across all states. It simulates various scenarios to ensure correct light signals are produced.

### Testbench Code
```verilog
module traffic_light_controller_tb;
// Testbench code here
endmodule
```

