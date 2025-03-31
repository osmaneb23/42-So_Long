# 🎮 So_long - A Simple 2D Game

Welcome to my **so_long** repository! This project is part of the **42 curriculum**, where I developed a simple 2D game in C using the MiniLibX graphics library. This project strengthened my understanding of graphics programming, event handling, game logic, and parsing handling.

---

## **✅ Project Validation**
- **Validated on:** September 15, 2024
- **Final Score:** 110/100
  - Achieved **bonus part** 🎉

---

## **📜 Project Overview**
The goal of this project was to create a 2D game where the player must collect all collectibles on the map and then reach the exit using the shortest possible route. The game features basic graphics rendering, keyboard controls, and map validation.

### **Key Requirements:**
- Create a graphical game using the MiniLibX library
- Implement player movement with W, A, S, D keys
- Parse and validate map files ending with `.ber` extension
- Handle collectibles that must be gathered before exiting
- Display movement count (steps taken by player)
- Ensure proper window management (closing, minimizing)
- Check for valid map configuration (walls, path validation)

### **Restrictions:**
- The project had to be coded in C
- Had to follow the 42 Norm (coding style guidelines)
- Could only use specific authorized functions:
  - open, close, read, write, malloc, free, perror, strerror, exit
  - Math library functions
  - MiniLibX functions
  - My own ft_printf function

---

## **🛠️ Implementation Details**

### **🎨 Graphics and Controls**
- Used MiniLibX for all graphical elements
- Implemented smooth window management
- Set up keyboard event handling for player movement
- Added ESC key and window close button functionality

### **🗺️ Map System**
- Created map parser to validate `.ber` map files
- Implemented path validation algorithm to ensure map is completable
- Handled various map error cases (invalid walls, missing elements)
- Supported the required map components:
  - `0`: Empty space (walkable)
  - `1`: Wall (obstacle)
  - `C`: Collectible
  - `E`: Exit
  - `P`: Player starting position

### **🎲 Game Logic**
- Implemented collision detection with walls
- Added collectible gathering mechanics
- Created exit validation (only accessible after getting all collectibles)
- Tracked player movement count
- **Bonus**: Displayed movement counter directly on game screen
  - Rendered the movement count in the game window
  - Updated in real-time with each valid player move

### **🧩 Code Structure**
- Organized code into logical modules:
  - Map parsing and validation
  - Graphics rendering
  - Player movement
  - Game state management
  - Event handling

---

## **🎮 Game Mechanics**
- **Objective**: Collect all items and reach the exit in the fewest steps possible
- **Controls**:
  - `W`: Move up
  - `A`: Move left
  - `S`: Move down
  - `D`: Move right
  - `ESC`: Exit game
- **Features**:
  - Visual display of movement counter (bonus feature)
  - Clean event handling
  - Map validation ensures a solvable game

---

## **🖼️ Screenshots & Examples**
The game features a top-down view with walls, collectibles, an exit, and a player character moving through the environment. Maps are parsed from `.ber` files that define the layout.

Example of a valid map:
```
1111111111111
10010000000C1
1000011111001
1P0011E000001
1111111111111
```

Legend:
- `1`: Wall
- `0`: Empty space
- `C`: Collectible
- `E`: Exit
- `P`: Player starting position

---

## **💻 Dependencies**
- **MiniLibX**: The game relies on this graphics library for rendering
  - X11 and Xext libraries are required for MiniLibX on Linux
- **C compiler**: gcc or cc with support for C standards

---

## **🔧 Installation & Usage**

### **📋 System Requirements**
- Linux-based operating system (developed on Linux)
- X11 window system
- C compiler (gcc/cc)

### **📥 Clone & Compile**
```
# Clone the repository
git clone https://github.com/osmaneb23/42-So_Long.git
cd 42-So_Long

# Compile the project
make
```

The Makefile handles all necessary compilation steps, including:
- Compiling all source files with `-Wall -Wextra -Werror` flags
- Linking with MiniLibX and X11 libraries
- Creating the executable

### **🚀 Running the Game**
```
# Run with a valid map file
./so_long maps/map.ber

# Try different maps
./so_long maps/another_map.ber
```

### **🧪 Testing Various Maps**
The repository includes several test maps in the `maps/` directory:
- Valid maps for normal gameplay
- Invalid maps to test error handling:
  - `map_coin_blocked.ber`: Map with unreachable collectibles
  - `map_empty.ber`: Empty map (should error)
  - `map_exit_blocked.ber`: Map with unreachable exit
  - `map_invalid_char.ber`: Map with invalid characters
  - `map_multiple_exits.ber`: Map with more than one exit

### **📋 Valid Map Requirements**
- Map must be rectangular and surrounded by walls
- Must contain exactly 1 exit (E)
- Must contain exactly 1 starting position (P)
- Must contain at least 1 collectible (C)
- Must have a valid path from player to all collectibles and to exit

### **⚠️ Error Handling**
The game provides specific error messages for different issues:
- Invalid map format or characters
- Multiple player positions or exits
- Missing required elements
- Unreachable collectibles or exit
- File reading errors

---

## **📂 Project Structure**
```
so_long/
│── src/                        # Source code directory
│   │── main.c                  # Entry point
│   │── draw.c                  # Rendering functions
│   │── map.c                   # Map handling functions
│   │── map_check.c             # Map validation
│   │── map_parsing.c           # Map parsing
│   │── player_moves.c          # Player movement handling
│   │── textures_init.c         # Texture initialization
│   │── get_next_line.c         # Line reading utility
│   │── get_next_line_utils.c   # Helper functions for get_next_line
│   │── utils.c                 # Utility functions 
│   │── utils_bis.c             # Additional utility functions
│   └── window.c                # Window management functions
│── includes/                   # Header files
│   └── so_long.h               # Main header
│── textures/                   # Game textures
│   │── coin16x16.xpm           # Collectible textures (multiple sizes)
│   │── coin32x32.xpm
│   │── coin64x64.xpm
│   │── coin128x128.xpm
│   │── exit16x16.xpm           # Exit textures (multiple sizes)
│   │── exit32x32.xpm
│   │── exit64x64.xpm
│   │── exit128x128.xpm
│   └── ...                     # More textures for player, walls, etc.
│── maps/                       # Example and test maps
│   │── map_coin_blocked.ber
│   │── map_empty.ber
│   │── map_exit_blocked.ber
│   │── map_invalid_char.ber
│   │── map_multiple_exits.ber
│   └── ...                     # More test maps
│── minilibx/                   # MiniLibX graphics library
└── Makefile                    # Compilation instructions
```

---

## **🎨 Bonus Implementation**
Instead of displaying movement count in the shell, I implemented the bonus feature to:
- Render the movement counter directly on the game screen
- Update the counter in real-time with each valid player move
- Format the display for clear visibility during gameplay

This enhancement required:
- Integration with MiniLibX's string rendering functions
- Careful positioning of the counter on the game window
- Managing the rendering layer to ensure visibility

---

## **⚠️ Limitations & Challenges**
- **MiniLibX Constraints**: The library has limited documentation and functionality compared to more modern graphics libraries
- **Memory Management**: Required careful handling of textures and map data to avoid leaks
- **Map Validation**: Implementing path finding to verify map solvability was challenging
- **Event Handling**: X11 event system required careful implementation

---

## **🎓 Key Learning Outcomes**
- **Graphics Programming:** Using the MiniLibX library for rendering
- **Game Development:** Creating game logic, collision detection, and state management
- **Map Parsing:** Reading and validating external data files
- **Path Validation:** Implementing algorithms to ensure map completability
- **Event Handling:** Managing keyboard and window events
- **Memory Management:** Properly allocating and freeing resources
- **Code Organization:** Structuring a more complex C project with multiple modules