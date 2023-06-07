# Day 3 Exploring the Dark

## Exploring the Dark

Show what you know about conditionals, and learn some new things about boolean logic! Teach the agent how to place torches for you, but only when there isn't already a block placed there.

## Step 1

First, grab a new ``||player.on chat command||`` block or edit the one that is already there to make a "light" command.

```blocks
player.onChat("light", function () {
    
})
```

## Step 2

The first thing the agent needs to do is move to the player, then take a step back. You'll need 2 blocks from the ``||agent||`` section to do this.

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
})
```

## Step 3

Can the agent place torches if it doesn't have any? No! Add a block that will give the agent some torches.

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
})
```

## Step 4

Now comes the conditional! The agent will place a torch, but only some of the time, when certain conditions are met.

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
    if(){
    }
})
```

## Step 5

We need to make sure there is NOT already a block in the way before we can place a block, so we will need a new block in our ``||logic.if||``. Try to find the ``||logic.not||`` block to put in the condition! Then, add ``||agent.agent detect block||`` inside the ``||logic.not||`` block.

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
    if(!agent.detect(AgentDetection.block, FORWARD)){
    }
})
```

## Step 6

If there is NOT a block detected in front of the agent, the space must be clear to place a torch. Add a block to place the torch!

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
    if(!agent.detect(AgentDetection.block, FORWARD)){
        agent.place(FORWARD)
    }
})
```

## Step 7

If there isn't room to place a torch, it would be helpful to get a message letting us know that. How can we do this? (Hint: we need to press the plus sign at the bottom of the ``||logic.if||``)

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
    if(!agent.detect(AgentDetection.block, FORWARD)){
        agent.place(FORWARD)
    } else {

    }
})
```

## Step 8

If there isn't room to place a torch, it would be helpful to get a message letting us know that. How can we do this? (Hint: we need to press the plus sign at the bottom of the ``||logic.if||`` and add a block that will send a message!)

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
    if(!agent.detect(AgentDetection.block, FORWARD)){
        agent.place(FORWARD)
    } else {
        player.say("There's a block in the way!")
    }
})
```

## Finished Code

Good job! You showed off what you know about conditionals, and if/else blocks! Now try the bonus!

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
    if(!agent.detect(AgentDetection.block, FORWARD)){
        agent.place(FORWARD)
    } else {
        player.say("There's a block in the way!")
    }
})
```

## Bonus

In the last activity, we used a variable and a forever loop to control the agent moving through a maze. Can you use that strategy here to make the agent follow the player and keep placing torches? (Hint: try using a ``||loops.pause||`` block to slow down how often the agent tries to place a torch!)

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
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
    if(!agent.detect(AgentDetection.block, FORWARD)){
        agent.place(FORWARD)
    } else {
        player.say("There's a block in the way!")
    }
    loops.pause(3000)
}
    
})
```

## Activity Complete!

You did it! Good work with that bonus challenge! 
