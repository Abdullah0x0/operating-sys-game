# Cosmic Conflict - OS Concepts Game

## Game Summary

*Cosmic Conflict* is a platform combat game where players face waves of alien enemies while embodying real-world OS principles through gameplay. Every mechanic—from enemy spawning to power-up management—is backed by multiprocessing, threading, IPC, and synchronization, giving players an interactive lens into how operating systems function under the hood.

## Gameplay Preview

<p align="center">
  <img width="1192" alt="Intro" src="https://github.com/user-attachments/assets/74487ae5-8b79-4e30-9f23-61d1774eb2f2" /><br>
  <strong><em>Intro Screen – Title and prompt to begin</em></strong>
</p>

&nbsp;

<p align="center">
  <img width="1192" alt="Wave 1" src="https://github.com/user-attachments/assets/40ab2d09-6512-4dc6-a1c7-499266395e37" /><br>
  <strong><em>Gameplay – Wave 1: First enemy encounter</em></strong>
</p>

&nbsp;

<p align="center">
  <img width="1192" alt="Wave 2" src="https://github.com/user-attachments/assets/492556bc-754b-4ead-b086-42cfab52a04e" /><br>
  <strong><em>Gameplay – Wave 2: Increased difficulty</em></strong>
</p>

&nbsp;

<p align="center">
  <img width="1192" alt="Info Toggle Placeholder" src="https://github.com/user-attachments/assets/9c88c683-4fcd-450b-b930-41b6d0736648" /><br>
  <strong><em>Info Toggle – Toggle real-time info overlay</em></strong>


&nbsp;

<p align="center">
  <img width="1192" alt="Debug Mode" src="https://github.com/user-attachments/assets/44060520-6185-451a-9659-0f1fa6becc84" /><br>
  <strong><em>Debug Overlay – Toggle real-time metrics</em></strong>
</p>

&nbsp;

<p align="center">
  <img width="1192" alt="Game Over" src="https://github.com/user-attachments/assets/9ff7e881-0704-4710-b6d2-2b987b84cadc" /><br>
  <strong><em>Game Over Screen – Final stats and reset prompt</em></strong>
</p>

## Demo Video

Watch a short gameplay showcase of *Cosmic Conflict* in action:

📺 [Demo Video on YouTube](https://www.youtube.com/watch?v=seFcBxCVnWg)

## OS Concepts Implemented

> **Note on Implementation Level**: The current implementation utilizes Python's high-level abstractions for operating system concepts. We are actively working to transition these implementations to more low-level approaches that better demonstrate the underlying operating system principles. As such, some features may be added, removed, or modified as we refine the implementation.

1. **Process Management**
   - Separate processes for game logic and rendering using Python's multiprocessing
   - Process synchronization through shared memory
   - Proper process initialization and termination handling

&nbsp;

<p align="center">
  <img width="618" alt="image" src="https://github.com/user-attachments/assets/4587e65a-ed2b-497e-81f8-19fd75f47cda" />

<br>
  <strong><em>Process creation and management using Python's multiprocessing module, demonstrating proper process initialization and daemon process handling.</em></strong>
</p>

&nbsp;

2. **Thread Management**
   - Multiple concurrent threads handling:
     - Background animations
     - Enemy AI and spawning
     - Power-up generation
     - Particle effects
   - Daemon threads for automatic cleanup
   - Thread-safe resource access

&nbsp;
  
<p align="center">
  <img width="489" alt="image" src="https://github.com/user-attachments/assets/ee595ecc-e568-4473-82c6-a74a9638478f" />
<br>
  <strong><em>Thread management implementation showing daemon thread creation for enemy spawning and power-up generation.</em></strong>
</p>

&nbsp;

3. **Synchronization Mechanisms**
   - Mutex locks for critical sections:
     - Entity management (`entities_lock`)
     - Wave management (`wave_lock`)
     - Shared resource access (`player_score_lock`, etc.)
   - Context managers for proper lock handling
   - Race condition prevention

&nbsp;
  
<p align="center">
  <img width="495" alt="image" src="https://github.com/user-attachments/assets/8a283730-b99c-496b-adef-728d5fd672e7" />
<br>
  <strong><em>Synchronization implementation using mutex locks for thread-safe entity creation and management.</em></strong>
</p>

&nbsp;

4. **Inter-Process Communication (IPC)**
   - Shared Memory:
     - Game state management
     - Player statistics (health, score)
     - Position tracking
   - Message Queues:
     - Input event handling
     - Game state updates
     - Entity synchronization

&nbsp;
    
<p align="center">
  <img width="529" alt="image" src="https://github.com/user-attachments/assets/dd0c0369-b27f-47ce-a65b-a62c0b0328e4" />
<br>
  <strong><em>Inter-process communication implementation using message queues for input handling and game state updates.</em></strong>
</p>

&nbsp;

5. **Resource Management**
   - Memory allocation and deallocation
   - Shared resource coordination
   - Safe process/thread termination
   - Asset loading and management
   - Sound and music system with dynamic loading

6. **Audio System**
   - Sound effect management
   - Dynamic sound loading and playback
   - Context-sensitive audio feedback based on game events
   - Adaptive volume based on event significance

7. **Signal Handling**
   - Implementation of SIGINT (Ctrl+C) handling for graceful shutdown
   - Signal routing to manage process termination sequence
   - Clean resource release during abnormal termination
   - Preventing orphaned processes and memory leaks

&nbsp;
  
<p align="center">
  <img width="351" alt="image" src="https://github.com/user-attachments/assets/dba67b35-255e-4b32-b4f4-9dc0a0d2e419" />

<br>
  <strong><em>Signal handling implementation showing graceful shutdown handling for SIGINT (Ctrl+C). </em></strong>
</p>

&nbsp;


8. **Context-Based Lock Management**
   - Advanced lock acquisition using context managers (with statements)
   - Automatic lock release even during exceptions
   - Deadlock prevention through consistent lock acquisition order
   - Minimized critical sections for improved performance

9. **Process Prioritization**
   - Daemon process implementation for automatic cleanup
   - Process hierarchy with parent-child relationships
   - Background vs. foreground process handling
   - Resource allocation based on process importance

11. **Event-based Programming Model**
    - Event-driven architecture for game interactivity
    - Polling and interrupt-based event handling
    - Event queues and dispatching systems
    - Asynchronous event processing similar to OS interrupt handling

12. **Advanced Queue-based Message Passing**
    - Structured inter-process message protocols
    - Priority-based message queue processing
    - Non-blocking message handling
    - Message filtering and routing between processes

## Technical Architecture

### Core Components
- `main.py` - Entry point and process orchestration
- `game_logic.py` - Game mechanics and entity management
- `renderer.py` - Graphics pipeline and display handling
- `entities.py` - Game object definitions and behaviors

### Process Structure
```
Main Process
├── Game Logic Process
│   ├── Enemy Spawner Thread
│   ├── Power-up Spawner Thread
│   └── Physics Update Thread
└── Renderer Process
    ├── Animation Thread
    ├── Particle System Thread
    └── Sound Effect System
```

## Setup and Installation

1. Requirements:
   - Python 3.8 or higher
   - Pygame library
   - Multiprocessing support

2. Installation:
   ```bash
   pip install -r requirements.txt
   ```

3. Running the game:
   ```bash
   python run_game.py
   ```

## Game Features

- Wave-based combat system with increasing difficulty
- Dynamic enemy AI with multiple behavior patterns
- Platform-based movement mechanics
- Power-up system with various effects
- Particle effects for visual feedback
- Real-time process/thread statistics display
- Smart platform generation ensuring reachability

## Gameplay Details

### Waves
- The game features a progressive wave system that increases in difficulty
- Each wave introduces more enemies with enhanced abilities
- Wave progression is shown with on-screen notifications
- Higher waves feature elite enemies with special abilities and increased health

### Enemy Types
1. **Basic Enemy (Type 1)**
   - Circular shape with basic movement patterns
   - Color changes from gray (wave 1) to red (wave 3+)
   - Elite versions feature glowing auras and teeth

2. **Tough Enemy (Type 2)**
   - Square shape with higher health
   - Color changes from dark blue (wave 1) to deep blue (wave 3+)
   - Elite versions have armor plates and glowing eyes

3. **Fast Enemy (Type 3)**
   - Triangle shape with rapid movement
   - Color changes from dark green (wave 1) to bright green (wave 3+)
   - Enhanced versions leave motion trails

### Weapons
1. **Primary Weapon**
   - Fast-firing blue energy bolts
   - Quick cooldown and medium damage
   - Visible blue particle trails

2. **Secondary Weapon**
   - Powerful green plasma balls
   - Slower fire rate but higher damage
   - Creates green particle effects

### Power-ups
1. **Health (Green)**
   - Restores player health
   - Green cross symbol with pulsing animation
   - Creates expanding ring effect when collected

2. **Score Boost (Yellow)**
   - Grants bonus points
   - Yellow star symbol with rotating animation
   - Creates rising particle effects when collected

3. **Invincibility (Blue)**
   - Temporary invulnerability to damage
   - Blue shield symbol with shield rotation effect
   - Creates expanding blue rings when collected

### Sound Effects
- Context-sensitive enemy defeat sounds based on enemy type
- Subtle sound for regular enemies, explosion sounds for elite enemies
- Different sound effects for various game events (powerups, shooting, etc.)
- Volume automatically adjusted based on event importance

### Visual Effects
- Dynamic particle systems for explosions and projectiles
- Expanding ring animations for power-up collection
- Enemy-specific death animations based on type and wave
- Glowing effects for elite enemies
- Parallax starfield background with nebula effects

### Player Controls
- **Arrow Keys** - Move the player and jump
- **Z** - Fire primary weapon
- **X** - Fire secondary weapon
- **ESC** - Pause game
- **P** - Toggle process info display
- **D** - Toggle platform reachability debug visualization
- **Q** - Quit game

## Implementation Details

### Synchronization
- Mutex locks prevent race conditions in entity updates
- Message queues handle inter-process communication
- Shared memory manages game state across processes

### Resource Management
- Texture and sound assets loaded once and shared
- Memory-efficient particle system
- Automatic resource cleanup on exit

### Performance Considerations
- Optimized collision detection
- Efficient entity management system
- Background thread pooling for resource operations

### Platform Generation Algorithm
The game implements a smart platform generation algorithm that ensures platforms are always reachable by the player:

1. Calculates the maximum jump height based on physics constants (jump power and gravity)
2. Places platforms only at heights reachable from at least one existing platform
3. Ensures adequate horizontal spacing for effective gameplay
4. Provides debug visualization (press 'D' in-game) to show platform reachability

## Next Steps and Final Demo Plans

Implementation of lower-level operating system concepts will be explored, both by introducing new mechanisms and by refactoring existing features. Abstractions such as Python’s `Queue` and `multiprocessing` will be reconsidered in favor of lower-level alternatives including shared memory segments, pipes, and POSIX-like signals. Development will proceed iteratively, allowing each stage of implementation to inform subsequent strategies and objectives for deeper systems-level integration.

- 🎯 **Leaderboard System**  
  Add a persistent leaderboard using shared memory to store high scores across sessions.

- ⚙️ **Lower-Level OS Features**  
  Addressing feedback to implement deeper OS integration:
  - Replace high-level Python multiprocessing with `multiprocessing.shared_memory` or `ctypes` for manual memory mapping.
  - Implement POSIX-like signaling using Python's `signal` module (e.g., `SIGUSR1`, `SIGTERM`) to control process behaviors.
  - Swap `Queue`-based IPC with raw pipes or sockets to reflect true message passing.
  - Other updates will continue through the development process.

These additions will be showcased in the final demo with the developer overlay enabled for live system behavior introspection.
