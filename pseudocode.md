# FROG-OF-WAR

// 1. Start
Start Game initialization Process

// 2. Input
    Take the following inputs:
        - Player actions (UP, DOWN, LEFT, RIGHT)
        - Player power-up activation (RAND KEY)
        - Game settings (level selection, difficulty)

// 3. Process
    Initialize game assets and settings 
    Define player starting position, lives, score
    Load game assets (graphics, sounds, levels)

// Main Game Loop (runs while player has lives)
    WHILE playerLives > 0:

    // Load current level
        Display level introduction for currentLevel
        Load obstacles and layout for currentLevel
        Set environment based on currentLevel theme

    // Level gameplay loop (runs until player completes level)
        WHILE level not complete:
            
            // Render Game visuals
            Display player, bstacles, collectibles, and UI

            // Handle player input
            IF player presses UP:
                Move player up if no obstacle collision
            IF player presses DOWN:
                Move player down if no obstacle collision
            IF player presses LEFT:
                Move player left if no obstace collision
            IF player presses RIGHT:
                Move player right if no obstacle collsion
            IF player presses POWER-UP:
                Activate POWER-UP

            // Update obstacle positions
            FOR each obstacle in level:
                Move obstacle based on its pattern
                IF obstacle moves off-screen:
                    Reset obstacle position

            // Check collisions    
            IF player collides with obstacle:
                IF POWER-UP is active:
                    Destroy obstacle
                ELSE:
                    Decrease playerLives by 1
                    Reset player position to start of level
            If player collides with POWER-UP:
                Apply collectible effect (increase score, give POWER-UP)

            // Check if player has reached the goal
            IF player position is at level goal:
                Set level complete to TRUE
                Add points based on level time and colectibes

        // Level complete
        Display level comltion screen
        Increment level number by 1 to load the next level

    // Game over
    Display game over screen
    IF player chooses to retry:
        Restart game wth initiaizeGame function
// 4. Output
    Produce the following outputs:
        - Display visuals of player movement, obstacles, collectibles
        - Show current score, lives, and POWER-UP status on UI
        - Display level completion and game over screens with player score

// 5. End
End game Process when player choose to quit

