# Day 3 Exploring the Dark

## Exploring the Dark

Show what you know about conditionals, and learn some new things about boolean logic! Teach the agent how to place lights for you, but only when there isn't already a block placed there.

## Step 1

First, grab a new ``||player.on chat command||`` block or edit the one that is already there to make a "light" command.

```blocks
player.onChat("light", function () {
    
})
```

## Step 2

The first thing the agent needs to do is move to the player. You'll need a block from the ``||agent||`` section to do this.

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
})
```

## Step 3

Can the agent place a light if it doesn't have any? No! Add a block that will give the agent some glowstone or another light block of your choice.

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.setItem(GLOWSTONE, 64, 1)
})
```

## Step 4

Now comes the conditional! The agent will place a light, but only some of the time, when certain conditions are met. Add the block that will do this!

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.setItem(GLOWSTONE, 64, 1)
    if(true){
    }
})
```

## Step 5

We need to make sure there is NOT already a block in the way before we can place a block, so we will need a way to say "not" in the condition of our ``||logic.if||``. Try to find the ``||logic.not||`` block to put in the condition! Then, add ``||agent.agent detect block||`` inside the ``||logic.not||`` block. Check for a block on the LEFT or RIGHT!

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.setItem(GLOWSTONE, 64, 1)
    if(!agent.detect(AgentDetection.block, LEFT)){
    }
})
```

## Step 6

If there is NOT a block detected beside the agent, the space must be clear to place a light. Add a block to place the light! Make sure the direction matches the direction you checked in the if!

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.setItem(GLOWSTONE, 64, 1)
    if(!agent.detect(AgentDetection.block, LEFT)){
        agent.place(LEFT)
    }
})
```

## Step 7

If there isn't room to place a light, it would be helpful to get a message letting us know that. How can we do this? (Hint: we need to press the plus sign at the bottom of the ``||logic.if||`` and add a block that will send a message!)

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.setItem(GLOWSTONE, 64, 1)
    if(!agent.detect(AgentDetection.block, LEFT)){
        agent.place(LEFT)
    } else {
        player.say("No room for a light!")
    }
})
```

## Finished Code

Good job! You showed off what you know about conditionals, and if/else blocks! Now try the bonus!

## Bonus

In the last activity, we used a variable and a forever loop to control the agent moving through a maze. Can you use that strategy here to make the agent follow the player and keep placing lights? (Hint: try using a ``||loops.pause||`` block to slow down how often the agent tries to place a torch!)

```blocks
let torching = 0
player.onChat("light", function () {
    torching = 1
})
player.onChat("stop", function () {
    torching = 0
})
loops.forever(function(){
if(torching == 1){
    agent.teleportToPlayer()
    agent.setItem(GLOWSTONE, 64, 1)
    if(!agent.detect(AgentDetection.block, LEFT)){
        agent.place(LEFT)
    } else {
        player.say("No room for a light!")
    }
    loops.pause(3000)
}
    
})
```

## Activity Complete!

You did it! Good work with that bonus challenge! 
