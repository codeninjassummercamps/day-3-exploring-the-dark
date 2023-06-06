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
    if(and){
    }
})
```

## Step 5

We need to make sure there is not already a block in the way before we can place a block, so we will need a new block in our ``||logic.if||``. Try to find the ``||logic.not||`` block to put in the condition! Then, add ``||agent.agent detect block||`` inside the ``||logic.not||`` block.

```blocks
player.onChat("light", function () {
    agent.teleportToPlayer()
    agent.move(BACK, 1)
    agent.setItem(TORCH, 64, 1)
    if(!agent.detect(AgentDetection.block, FORWARD)){
    }
})
```

## Finished Code

Good job listening to Sensei, you can check your code with the hint. Now try the bonus!

```blocks
let going = 0
player.onChat("maze", function () {
    agent.teleport(world(-7, 0, -3), NORTH)
    going = 1
})
loops.forever(function(){
    if(going == 1){
        if(agent.detect(AgentDetection.Block, FORWARD)){
            agent.turn(TurnDirection.Right)
        }else{
            agent.move(FORWARD, 1)
        }
    }
})
```

## Bonus

The agent can get into the maze and get to the center, but what happens in the center? First, try making a way to stop the agent from moving using a chat command. Once you've tried that, what can you do to teach the agent to get back out of the maze? This is a really tricky challenge, but if there is time, your Senseis can show you how to do it!

```blocks
player.onChat("stop", function () {
    going = 0
})
```

## Activity Complete!

You did it! You explored new conditionals and learned about the ``||logic.else||`` part of a conditional! 
