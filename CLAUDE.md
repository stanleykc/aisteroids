# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Asteroid Blaster is a classic arcade-style space shooter game built as a single HTML file using HTML5 Canvas and vanilla JavaScript. The game features realistic physics, procedural asteroid generation, and particle effects.

## Architecture

### Single-File Structure
- **Main File**: `asteroid_blaster.html` (lines 1-577) - Contains HTML, CSS, and JavaScript in a single file
- **HTML Structure**: Game canvas, score display, and game over overlay (lines 70-81)
- **CSS Styling**: Dark space theme with gradients and responsive design (lines 7-67)
- **JavaScript Game Engine**: Object-oriented ES6 classes with game loop (lines 83-576)

### Core Game Objects

#### Ship Object (`asteroid_blaster.html:95-106`)
- Global ship object with position, velocity, rotation, and physics properties
- No class definition - uses plain object with properties

#### Class Architecture
- **Laser Class** (`asteroid_blaster.html:126-152`): Projectile physics with lifetime management
- **Asteroid Class** (`asteroid_blaster.html:154-306`): Three-generation system (Large → Medium → Small) with procedural rendering
- **Particle Class** (`asteroid_blaster.html:308-332`): Explosion effects with physics simulation

### Game Systems

#### Physics Engine
- Velocity-based movement with friction and thrust mechanics
- Circle-based collision detection between all objects
- Screen wrapping for seamless boundaries

#### Rendering System
- Canvas 2D context with procedural asteroid art
- Gradient lighting, particle effects, and thrust flames
- Realistic asteroid textures with craters and surface details

#### Game State Management
- Global variables for game state (`gameRunning`, `score`, `keys`)
- Arrays for game objects (`lasers`, `asteroids`, `particles`)
- Event-driven input handling with keyboard state tracking

## Development Workflow

### Testing the Game
- Open `asteroid_blaster.html` directly in any modern web browser
- No build process, dependencies, or server required
- Compatible with Chrome, Firefox, Safari, Edge (requires HTML5 Canvas support)

### Game Controls
- **Arrow Keys**: Left/Right to rotate, Up to thrust
- **Spacebar**: Fire laser (limited to 5 concurrent lasers)
- **Play Again Button**: Restart after game over

### Key Game Features
- **Fragmentation System**: Large asteroids break into 2-3 smaller pieces when hit
- **Scoring**: Large (50 points), Medium (25 points), Small (10 points)
- **Progressive Difficulty**: Asteroid spawn rate increases over time (starts at 1200ms, decreases to minimum 20ms)
- **Particle Effects**: 10 particles per asteroid explosion with physics

## Code Patterns

### Object Creation
- Ship uses global object literal
- Game entities use ES6 classes with constructor parameters
- Procedural generation for asteroid shapes and properties

### Game Loop Pattern
- `requestAnimationFrame` for 60 FPS rendering
- Update → Physics → Collision → Render cycle
- Array management with reverse iteration for safe removal

### Collision Detection
```javascript
function checkCollision(obj1, obj2, radius1, radius2) {
    const dx = obj1.x - obj2.x;
    const dy = obj1.y - obj2.y;
    const distance = Math.sqrt(dx * dx + dy * dy);
    return distance < radius1 + radius2;
}
```

## Performance Considerations

- Object pooling for particles and projectiles
- Boundary culling for off-screen objects
- Optimized canvas rendering with minimal state changes
- Collision optimization with early exit conditions

## Common Modifications

When modifying the game:
- All code is in the single `asteroid_blaster.html` file
- Game state is managed through global variables and arrays
- Visual changes are handled through Canvas 2D context drawing
- Physics modifications affect object velocity and position properties
- New game objects should follow the existing class pattern with `update()` and `draw()` methods