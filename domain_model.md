
```mermaid
classDiagram
    class Player {
        + move()
        + navigateMaze()
        + detectEnemy()
        + takeDamage()
        + die()
    }
    
    class Enemy {
        + detectPlayer()
        + followPlayer()
        + shoot()
    }
    
    class EnemyProjectiles {
        + move()
        + collideWithPlayer()
        + collideWithWalls()
        + dealDamage()
    }
    
    class Walls {
        + blockMovement()
        + blockProjectiles()
    }
    
    class Light {
        + illuminatePlayer()
        + turnOff()
        + affectEnemyVision()
    }
    
    class Camera {
        + followPlayer()
        + adjustView()
    }
    
    class Health {
        + trackHealth()
        + takeDamage()
        + triggerDeath()
    }
    
    class GameState {
        + trackState()
        + transitionState()
        + handleEvents()
    }
    
    Player --> Enemy : "detected by"
    Player --> Health : "has"
    Player --> GameState : "tracked by"
    Player --> EnemyProjectiles : "takes damage from"
    Enemy --> VisionCone : "has"
    Enemy --> EnemyProjectiles : "shoots"
    EnemyProjectiles --> Walls : "collides with"
    EnemyProjectiles --> Player : "collides with"
    Light --> Enemy : "affects vision"
    GameState --> Camera : "adjusts view based on state"
    GameState --> Player : "controls game state"
    GameState --> Health : "ends game when health is zero"
    Camera --> Player : "follows"
    Walls --> Maze : "part of"
