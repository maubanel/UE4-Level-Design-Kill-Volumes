<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Extending Player Events

<sub>[previous](../) • [home](../README.md#user-content-ue4-animations) • [next](../)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

In this final chapter of the walkthrough, we'll be implementing the Player Death and Respawn Events.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

We’ll be making two Custom Events, one for the Death state and the other for Respawn. Move to the <b>BP_ThirdPersonCharacter</b> Blueprint and right click on the graph to create a <b>Custom Event</b> node. Name this one <b>Death</b>. Go ahead and create a Custom Event for <b>Respawn</b> as well.

<img src="images/2021-11-18 11_28_58-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

We’ll start with the Death event. From the Death Event, drag out a <b>Set Simulate Physics (Mesh)</b> node. Set Simulate to <b>True</b>. This will enable the ragdoll effect upon colliding with the volume. From here we can connect a <b>Print String</b> node to get some debug information.  Type in `Death` as the string.

<img src="images/2021-11-18 11_42_58-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

From the Print String, pull off a <b>Disable Input</b> node. This will make it so that the player cannot controller the character while it’s “dying.” This node needs an input, so make a <b>Get Player Controller</b> node and connect it to the Player Controller input.

<img src="images/2021-11-23 10_04_33-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Finally we just need to add a <b>Delay</b> node before respawning our character. I set the Delay duration to <b>2.0</b>. From the Completed node, drag out your <b>Respawn</b> event.

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

That’s it for the Death event, now we can fill out the Respawn event. Respawn will do a couple of things: 1.) saving the player’s last position, 2.) reattach the capsule component, 3.) re-enable player controls.

Start off by making a new variable called <b>LastPosition</b> of type Transform.

<img src="images/2021-11-23 09_18_55-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Move your graph to the Respawn Custom Event that you made, and drag off a <b>SetActorTransform</b> node. Drop in your (Get) <b>LastPosition</b> variable and connect it to the <b>New Transform</b> input.

<img src="images/2021-11-23 09_21_46-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

From the SetActorTransform, create a <b>SetSimulatePhysics (Mesh)</b> and leave this value at <b>False</b>. Becauce we enabled the ragdoll effect in the Death event, this will put the physics back into the player’s control.

Now drag off an <b>AttachComponentToComponent (Mesh)</b> from the Set Simulate Physics. The Target should be the Mesh component. For the Parent, pull in a copy of the <b>Capsule Component</b>.

<img src="images/2021-11-23 09_30_28-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we can place the Player at a new position on the level upon respawning. From the Attach node, create a <b>SetRelativeLocationAndRotation (Mesh)</b> node. For my new location, I chose <b>(0, 0, -97)</b> and for rotation I chose <b>(0, 0, 270)</b>. Set these accordingly to how your level is setup.

Finally, we’ll need to reenable player input. From the SetRelativeLocationAndRotation node, drag off an <b>Enable Input</b> node. For the Player Controller input, create a new <b>Get Player Controller</b> node. 

<img src="images/2021-11-23 09_35_31-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now Compile everything and return to your scene. Hit Play and let’s see what we get:

https://user-images.githubusercontent.com/20305074/143072944-06748818-00d9-4087-8ddf-5864d3de19f1.mp4


<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`ITA`| :large_blue_diamond:

That’s all for this walkthrough! <b>Save All and Commit</b> to source control.
___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=FINISHED!">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../kill-volume-event-graph/README.md#kill-volume-event-graph)| [home](../README.md#level-design-kill-volumes) 
|---|---|
