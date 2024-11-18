
edit
# Test Plan for **Frog of War**

## Part 1: Unit Testing the Game Mechanics

| **Test Case**               | **Test Data**                                  | **Expected Outcome**                                                                                                            |
|-----------------------------|------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| **Player Movement (Kratos/Atreus)**  | Pressing W, A, S, D (or I, J, K, L for alternative controls) | Kratos/Atreus should move smoothly in the respective direction on the screen. Movement should be constrained by the game boundaries. |
| **Jumping (Spacebar)**         | Pressing Spacebar to jump                      | Kratos/Atreus should jump to a predefined height and distance, based on the level's terrain (e.g., obstacles).                    |
| **Combat Mechanic (Leviathan Axe / Bow)** | Pressing a designated attack button (e.g., Spacebar or other) | The Leviathan Axe or Atreus' bow should hit enemies in range and cause appropriate damage or effects (e.g., stun, knockback).     |
| **Collision Detection**       | Kratos/Atreus collides with enemies or environmental hazards | Upon collision with any hazard or enemy, Kratos/Atreus should take damage or be stopped. Enemies should also react correctly.     |
| **Level Transition**         | Completing a level or reaching the exit point | The game should properly transition to the next realm (level) with a smooth cutscene or transition animation.                    |

---

## Part 2: Logic Testing the Game Rules and Calculations

| **Test Case**                    | **Test Data**                                      | **Expected Outcome**                                                                                                                       |
|-----------------------------------|----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Score Calculation**             | Defeating enemies, avoiding hazards, completing levels | The player's score should increase accordingly based on the number of enemies defeated, hazards avoided, and levels completed.              |
| **Leviathan Axe Damage**          | Kratos hits an enemy with the Leviathan Axe        | The enemy should take a set amount of damage. If it is a boss or special enemy, a special damage calculation or effect (e.g., stagger) should trigger. |
| **Bow Damage (Atreus)**           | Atreus hits an enemy with the bow                  | The enemy should take a set amount of damage based on the bow's strength. If applicable, status effects like poison should apply.            |
| **Level Progression Speed**      | Player completes each realm/level                  | As the player advances, the game should gradually increase in difficulty, whether by increasing enemy strength, speed, or environmental hazards. |
| **Lives/Respawn Mechanism**      | Kratos/Atreus loses all lives or fails to complete a level | If the player runs out of lives or fails a level, a game-over screen should appear. If there are remaining lives, they should respawn at the appropriate point. |

---

## Part 3: Boundary Testing: Edge Cases and Limits

| **Test Case**                     | **Test Data**                                      | **Expected Outcome**                                                                                                                       |
|-----------------------------------|----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Maximum Score**                 | Score reaches maximum (e.g., 99999)                 | The score should stop increasing or be capped at the set maximum. The score should be displayed correctly on the HUD, without overflow.        |
| **Minimum Score**                 | Player loses all points or goes negative            | The score should not go negative. If the game allows for score decrement, it should stop at zero.                                         |
| **Level Boundaries (Realm Limits)**| Player tries to exit the left/right/top/bottom of the screen | Kratos/Atreus should be constrained to the visible area of the screen and should not pass through the boundaries.                         |
| **Player Collision with Hazard**  | Kratos/Atreus collides with an edge of the terrain | The player should be immediately stopped or pushed back slightly (if there's terrain interaction).                                          |
| **Multiple Enemies**             | Several enemies appear on-screen at once           | The game should be able to handle multiple enemies on the screen simultaneously without lag or crashes. Enemy behaviors should remain consistent. |

---

## Part 4: Integration Testing: System Interaction

| **Test Case**                     | **Test Data**                                      | **Expected Outcome**                                                                                                                       |
|-----------------------------------|----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Player Movement and Combat**    | Kratos moves and attacks simultaneously            | Movement and combat mechanics should work in tandem without interfering with each other. The player should not be able to move and attack at the same time. |
| **Level Transition (Next Realm)** | Player finishes a level, transitions to the next   | The player should be transitioned smoothly to the next realm with the correct environment and new enemies. The HUD should update accordingly. |
| **Score Update on Level Complete** | Player completes a level, score calculation triggers | After completing a level, the score should update based on performance, and the new level should begin with the score displayed correctly.    |
| **Audio and Visual Synchronization** | Kratos/Atreus performs an action (e.g., attack, jump) | The audio (sound effects) and visual animations (sprite effects, animations) should be synchronized during actions like attacks, jumps, and enemy deaths. |

---

## Part 5: Handling Bad Input and Run-Time Errors

| **Test Case**                     | **Test Data**                                      | **Expected Outcome**                                                                                                                       |
|-----------------------------------|----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Invalid Keypress**              | Pressing invalid keys or multiple keys at once     | The game should ignore non-mapped key presses or simultaneous key presses and not cause any crashes or misbehavior.                         |
| **Unexpected Player Input**       | Player presses unassigned keys, or key combination | Unassigned keys or key combinations should be ignored, and no unexpected behavior should occur (e.g., no crashes, menu popping up randomly). |
| **Game State Integrity**          | Player interrupts game (e.g., closing window)      | The game should handle unexpected state changes, like quitting mid-level, by either pausing or gracefully exiting without corrupting data.   |
| **Error Handling (Score Data)**   | Corrupt save file or unexpected system shutdown    | If the save file is corrupt, the game should display an error message and allow the player to start a new game without crashing.             |
| **Error Recovery**                | Server (or online) feature crashes or loses connection | If there's a loss of online connectivity (if applicable), the game should notify the player and allow them to return to the main menu. |

---

## Test Case Table

| **Test Case**                       | **Test Data**                                         | **Expected Outcome**                                                                                                             |
|-------------------------------------|-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| **Player Movement (Kratos/Atreus)** | Pressing WASD/IJKL                                     | Kratos/Atreus should move according to the keys pressed.                                                                          |
| **Jumping Mechanic**                | Pressing Spacebar                                     | Kratos/Atreus should jump with a specific height, depending on the terrain.                                                      |
| **Leviathan Axe Combat**            | Kratos attacks an enemy                               | The enemy should receive damage, and a damage number should appear on the screen.                                                 |
| **Bow Combat (Atreus)**             | Atreus attacks an enemy                               | The enemy should receive damage, and if necessary, be affected by any status effect (e.g., poisoned).                            |
| **Score Update**                    | Defeating an enemy                                   | The score should increase by a predefined amount (e.g., 100 points per enemy).                                                   |
| **Level Transition**                | Player reaches the level exit                        | The game should smoothly transition to the next realm, with appropriate animations and updates to the HUD.                        |
| **Multiple Enemies**                | Several enemies on screen                             | The game should be able to handle multiple enemies at once without issues such as lag or collision detection problems.             |
| **Invalid Key Input**               | Pressing random keys (e.g., `z', `g', etc.)           | Any invalid key input should be ignored, and the game should continue without crashing.                                           |
| **Audio/Visual Sync**               | Kratos attacks an enemy                              | The sound effect and the visual effect should occur simultaneously when Kratos attacks an enemy.                                  |
| **Server Loss (if applicable)**     | Losing connection during gameplay (online mode)       | The game should alert the player that the server is lost and return them to the main menu.                                        |

---

This test plan framework for **Frog of War** covers key game mechanics, logic, boundary scenarios, integration of systems, and error handling, ensuring a stable and functional game experience.
