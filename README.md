# 🦆 FLAPPY DUCK HUNTER

```
███████╗██╗      █████╗ ██████╗ ██████╗ ██╗   ██╗
██╔════╝██║     ██╔══██╗██╔══██╗██╔══██╗╚██╗ ██╔╝
█████╗  ██║     ███████║██████╔╝██████╔╝ ╚████╔╝ 
██╔══╝  ██║     ██╔══██║██╔═══╝ ██╔═══╝   ╚██╔╝  
██║     ███████╗██║  ██║██║     ██║        ██║   
╚═╝     ╚══════╝╚═╝  ╚═╝╚═╝     ╚═╝        ╚═╝   
                                                  
██████╗ ██╗   ██╗ ██████╗██╗  ██╗               
██╔══██╗██║   ██║██╔════╝██║ ██╔╝               
██║  ██║██║   ██║██║     █████╔╝                
██║  ██║██║   ██║██║     ██╔═██╗                
██████╔╝╚██████╔╝╚██████╗██║  ██╗               
╚═════╝  ╚═════╝  ╚═════╝╚═╝  ╚═╝               
                                                  
██╗  ██╗██╗   ██╗███╗   ██╗████████╗███████╗██████╗ 
██║  ██║██║   ██║████╗  ██║╚══██╔══╝██╔════╝██╔══██╗
███████║██║   ██║██╔██╗ ██║   ██║   █████╗  ██████╔╝
██╔══██║██║   ██║██║╚██╗██║   ██║   ██╔══╝  ██╔══██╗
██║  ██║╚██████╔╝██║ ╚████║   ██║   ███████╗██║  ██║
╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═══╝   ╚═╝   ╚══════╝╚═╝  ╚═╝
```

> **A brutal twist on the classic Flappy Bird formula**  
> Survive. Record. Hunt yourself down.

-----

## 🎮 GAME OVERVIEW

**Flappy Duck Hunter** is a dual-phase arcade game that combines reflex-based gameplay with precision shooting mechanics. Built with a neo-brutalist aesthetic featuring stark blacks, whites, and vibrant yellow accents, this game challenges you to first survive the gauntlet, then hunt down your own replay.

### 🎯 MISSION BRIEFING

**PHASE 1 - THE FLIGHT**  
Navigate through an endless obstacle course of randomly generated pipes. Each second survived = +1 point. Every move is recorded for Phase 2.

**PHASE 2 - THE HUNT**  
Watch your exact flight path replay in real-time. Click/tap to fire at your past self. Each second in hunting mode = -1 point. Hit the target before time runs out!

-----

## ✨ FEATURES

### 🎨 Neo-Brutalist Design

- **Stark color palette**: Black, White, Yellow
- **Thick borders** (4px) on all UI elements
- **Bold drop shadows** (8px offset)
- **Geometric shapes** with pixel-perfect rendering
- **High contrast** for maximum visual impact

### 🕹️ Dual-Phase Gameplay

- **Physics-based flight** with gravity and impulse controls
- **Time-stamped recording system** for perfect replay
- **Hitscan shooting mechanics** with 1-second cooldown
- **Dynamic scoring** (+1/sec in Phase 1, -1/sec in Phase 2)

### 🎵 Audio System

- **Flap sound** - Satisfying jump feedback
- **Collision sound** - Dramatic crash effect
- **Shoot sound** - Laser-like firing effect
- **Victory/Defeat music** - Unique end-game audio

### 🏆 High Score System

- **Persistent storage** using localStorage
- **New record detection** with animated badge
- **Shareable achievements**:
  - 💾 Download PNG badge
  - 📋 Copy formatted text to clipboard
  - 📤 Social media ready

### 📱 Mobile-First Design

- **Touch-optimized** controls
- **Responsive layout** adapts to all screen sizes
- **No scroll/zoom** interference
- **Fluid 60fps** performance

-----

## 🎯 CONTROLS

### Phase 1 - Flight

|Input               |Action           |
|--------------------|-----------------|
|**TAP** (Mobile)    |Flap wings / Jump|
|**CLICK** (Desktop) |Flap wings / Jump|
|**SPACE** (Keyboard)|Flap wings / Jump|

### Phase 2 - Hunt

|Input              |Action         |
|-------------------|---------------|
|**TAP** (Mobile)   |Fire projectile|
|**CLICK** (Desktop)|Fire projectile|
|**MOVE**           |Aim crosshair  |

-----

## 🔧 TECHNICAL SPECS

### Architecture

```
┌─────────────────────────────────────┐
│        GAME STATE MACHINE           │
├─────────────────────────────────────┤
│  Phase 0: Menu                      │
│  Phase 1: Flight (Recording)        │
│  Phase 2: Hunt (Replay + Shoot)     │
│  Phase 0: Game Over                 │
└─────────────────────────────────────┘
```

### Core Systems

- **Physics Engine**: Gravity-based bird movement
- **Collision Detection**: AABB (Axis-Aligned Bounding Box)
- **Recording System**: Frame-by-frame Y-coordinate array
- **Replay System**: Index-based position playback
- **Audio Engine**: Web Audio API with procedural synthesis
- **Rendering**: HTML5 Canvas with 2D context

### Game Constants

```javascript
GRAVITY: 0.6
JUMP_FORCE: -9
PIPE_SPEED: 2.5
PIPE_GAP: 130px (±30px variation)
PIPE_WIDTH: 60px
SHOT_COOLDOWN: 1000ms
```

### Performance

- **Target FPS**: 60
- **Canvas Resolution**: Adaptive (16:9 aspect ratio)
- **Memory Usage**: <10MB
- **Storage**: <1KB (high score only)

-----

## 🎲 GAMEPLAY MECHANICS

### Obstacle Generation

- **Random height**: Full canvas range (60px margins)
- **Variable gaps**: 100-160px randomization
- **Spawn rate**: Every 180px traveled
- **Difficulty curve**: Increases with faster pipes

### Scoring System

```
Flight Score = Survival Time (seconds)
Hunt Penalty = Time to Hit (seconds)
Final Score = Flight Score - Hunt Penalty
```

**Example:**

- Survived 15 seconds in Flight → Score: 15
- Took 8 seconds to hit target → Final: 15 - 8 = 7 points

### High Score Logic

```
IF current_score > stored_high_score:
    UPDATE high_score
    SHOW new_record_badge
    ENABLE share_button
```

-----

## 🏅 ACHIEVEMENT BADGES

When you beat your high score, generate a shareable badge:

```
┌─────────────────────────────┐
│                             │
│           🏆                │
│                             │
│   FLAPPY DUCK HUNTER        │
│                             │
│      ┌─────────┐            │
│      │   42    │            │
│      └─────────┘            │
│                             │
│   HIGH SCORE ACHIEVED       │
│                             │
└─────────────────────────────┘
```

**Format Options:**

- PNG image (600x600px)
- Clipboard text with emoji decorations

-----

## 🚀 QUICK START

### Installation

```bash
# No installation required!
# Simply open the HTML file in any modern browser
```

### Browser Support

- ✅ Chrome/Edge 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

### Requirements

- Modern browser with Canvas API support
- Web Audio API support
- localStorage enabled

-----

## 🎨 DESIGN PHILOSOPHY

### Neo-Brutalism Principles

1. **Function over form** - Every element serves a purpose
1. **Bold typography** - Thick, black font weights
1. **Stark contrast** - No gradients, no subtle shading
1. **Geometric shapes** - Squares, rectangles, hard edges
1. **Negative space** - Let elements breathe
1. **Strong shadows** - 8px offset for depth

### Color Theory

```
PRIMARY:   #FFFFFF (White) - Foreground elements
SECONDARY: #000000 (Black) - Borders & shadows
ACCENT:    #FACC15 (Yellow) - Highlights & actions
BACKGROUND:#18181B (Dark Gray) - Canvas background
```

-----

## 📊 DIFFICULTY ANALYSIS

### Beginner (0-5 points)

- Learning basic flap timing
- Understanding pipe patterns
- Getting comfortable with controls

### Intermediate (5-15 points)

- Consistent flapping rhythm
- Reading ahead to next obstacles
- Quick target acquisition in Phase 2

### Advanced (15-30 points)

- Mastery of momentum control
- Predictive obstacle navigation
- Sub-5 second hunting times

### Expert (30+ points)

- Frame-perfect inputs
- Optimal flight paths
- Instant target locks

-----

## 🐛 KNOWN FEATURES

These aren’t bugs, they’re *features*:

- Extremely challenging difficulty curve
- No tutorial (figure it out!)
- Brutally honest design
- Your past self haunting you

-----

## 🎯 DEVELOPMENT ROADMAP

### Future Enhancements

- [ ] Online leaderboards
- [ ] Daily challenges
- [ ] Custom skins
- [ ] Power-ups
- [ ] Multiplayer mode
- [ ] Speed run timer
- [ ] Combo scoring system

-----

## 📜 LICENSE

This game is free to play and share!  
Built with ❤️ using vanilla HTML, CSS, and JavaScript.

-----

## 🙏 CREDITS

**Design**: Neo-Brutalist aesthetic  
**Sounds**: Web Audio API procedural synthesis  
**Inspiration**: Flappy Bird + FPS mechanics  
**Built with**: HTML5 Canvas, Tailwind CSS, Pure JS

-----

## 🎮 FINAL WORDS

```
┌──────────────────────────────────────┐
│                                      │
│  "The only way to beat yourself      │
│   is to know yourself."              │
│                                      │
│  "Every death is a lesson.           │
│   Every replay is a teacher."        │
│                                      │
│  "Can you hunt what you once were?"  │
│                                      │
└──────────────────────────────────────┘
```

**NOW GO FORTH AND HUNT! 🦆🎯**

-----

*Made with maximum brutality and minimal mercy*  
*Version 1.0 | 2025*
