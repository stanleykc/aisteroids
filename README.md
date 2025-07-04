# Asteroid Blaster

A classic arcade-style asteroid blaster game built with HTML5 Canvas and JavaScript. Navigate your ship through space, blast asteroids into smaller pieces, and survive as long as possible while your score climbs higher.

## What This Program Does

**Asteroid Blaster** is a retro-style space shooter game where players:
- Control a triangular spaceship in 2D space
- Shoot lasers to destroy asteroids that spawn from screen edges
- Break large asteroids into smaller fragments for points
- Survive increasingly difficult waves of asteroids
- Compete for high scores with progressive difficulty scaling

### Game Features

- **Realistic Physics**: Ship movement with momentum, friction, and thrust mechanics
- **Dynamic Asteroids**: Procedurally generated asteroid shapes with realistic textures, craters, and surface details
- **Fragmentation System**: Large asteroids break into 2-3 smaller pieces when hit
- **Particle Effects**: Explosion particles when asteroids are destroyed
- **Progressive Difficulty**: Asteroid spawn rate increases over time
- **Score System**: Different point values for different asteroid sizes (Large: 50, Medium: 25, Small: 10)
- **Responsive Controls**: Smooth ship rotation and thrust with visual flame effects

### Controls

- **Arrow Keys**: 
  - Left/Right: Rotate ship
  - Up: Thrust forward
- **Spacebar**: Fire laser
- **Play Again Button**: Restart after game over

## How It's Implemented

### Technical Architecture

The game is built as a single HTML file containing:

1. **HTML Structure** (`asteroid_blaster.html:70-81`)
   - Canvas element for game rendering
   - Score display and game over overlay
   - Responsive layout with space-themed styling

2. **CSS Styling** (`asteroid_blaster.html:7-67`)
   - Dark space theme with gradient backgrounds
   - Responsive design centered on screen
   - Game UI elements (score, controls, game over screen)

3. **JavaScript Game Engine** (`asteroid_blaster.html:83-576`)
   - Object-oriented design with ES6 classes
   - Game loop with requestAnimationFrame for smooth 60 FPS
   - Collision detection and physics simulation

### Core Game Objects

#### Ship Object (`asteroid_blaster.html:95-106`)
- Position, velocity, and rotation tracking
- Physics properties (thrust, friction, max speed)
- Wrapping screen boundaries

#### Laser Class (`asteroid_blaster.html:126-152`)
- Projectile physics with lifetime management
- Screen wrapping behavior
- Collision detection with asteroids

#### Asteroid Class (`asteroid_blaster.html:154-306`)
- **Generational System**: 3 generations (Large → Medium → Small)
- **Procedural Generation**: Random sizes, velocities, and rotations
- **Realistic Rendering**: Irregular shapes with gradients, craters, and surface textures
- **Fragmentation Logic**: Breaks into 2-3 smaller asteroids when destroyed

#### Particle Class (`asteroid_blaster.html:308-332`)
- Explosion effects with physics simulation
- Lifetime management and alpha blending

### Game Systems

#### Physics Engine
- **Movement**: Velocity-based movement with friction
- **Collision Detection**: Circle-based collision between all objects
- **Screen Wrapping**: Seamless world boundaries

#### Rendering System
- **Canvas 2D Context**: Hardware-accelerated graphics
- **Procedural Art**: Asteroids with unique shapes and textures each game
- **Visual Effects**: Gradient lighting, particle systems, thrust flames

#### Game State Management
- **Input Handling**: Keyboard event listeners with key state tracking
- **Game Loop**: Update → Physics → Collision → Render cycle
- **Difficulty Scaling**: Dynamic asteroid spawn rate adjustment

### Performance Optimizations

- **Object Pooling**: Efficient memory management for particles and projectiles
- **Boundary Culling**: Objects removed when off-screen too long
- **Collision Optimization**: Early exit conditions and radius-based detection
- **Rendering Efficiency**: Minimal canvas state changes and optimized drawing calls

## Getting Started

1. Open `asteroid_blaster.html` in any modern web browser
2. Use arrow keys to move and spacebar to shoot
3. Survive as long as possible and achieve a high score!

## Browser Compatibility

- Chrome, Firefox, Safari, Edge (all modern versions)
- Requires HTML5 Canvas support
- No external dependencies or libraries needed
