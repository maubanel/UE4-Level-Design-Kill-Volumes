<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Kill Volume Event Graph

<sub>[previous](../base-mesh/README.md#) • [home](../README.md#) • [next](../extending-player-events/README.md#)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

In this chapter we'll be setting up the functionality of our kill volume by laying out the event graph.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

In the event graph of the Kill Volume Blueprint, we’ll be calling the Player Death Event upon collision. This is a simple, two-step process. From the <b>Actor Begin Overlap</b> node, drag out a <b>Cast to BP_ThirdPersonCharacter</b>. From this cast, drag off a <b>Death</b> event. Feed the <b>As Third Person Character</b> from the previous node into Death Event’s Target input.

<img src="images/2021-11-18 10_25_47-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond:

Next we just need to actually access the Player Pawn for the Cast we made. Just create a <b>Get Player Pawn</b> node and feed it into the Object input of the Cast. Your graph should look something like this:

<img src="images/2021-11-18 10_28_57-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

And that’s all for the base functionality. Let’s add an option to turn the Mesh on and off (because we don’t actually need to see the volume in game, as only the collision is what’s driving the interaction). In the Variables section, create a new Boolean called <b>bShowVolume</b>. Make it <b>Private</b> and <b>Instance Editable</b>.

<img src="images/2021-11-18 10_41_01-UE4LevelDesignExtras - Unreal Editor - Copy.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Compile and drag in a copy of your ShowVolume variable. Create a <b>Branch</b> node from the <b>Event BeginPlay</b> and connect ShowVolume to the condition input.

<img src="images/2021-11-18 10_44_47-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Set your Show Volume’s default value to <b>True</b>.

<img src="images/show volume.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

From the <b>True</b> branch, create a <b>Destroy Component (Cube)</b>. Compile and save. Your final graph should look like this:

<img src="images/2021-11-18 10_46_18-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

That’s all for this Blueprint. Now we can complete the functionality by extending the Death and Respawn Events for our Player.

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Extending Player Events">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../base-mesh/README.md#creating-the-base-mesh)| [home](../README.md#level-design-kill-volumes) | [next](../extending-player-events/README.md#extending-player-events)|
|---|---|---|
