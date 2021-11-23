<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Creating the Base Mesh

<sub> [home](../README.md#) • [next](../kill-volume-event-graph/README.md#)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

The first thing we'll need is an actual "volume" that will exist in the scene and trigger the necessary player events.

<br>

---


##### `Step 1.`\|`ITA`|:small_blue_diamond:

Right click in your `Content Browser | Blueprints` folder and make a new Actor Blueprint. Name it <b>BP_KillVolume</b>.

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

Let’s add two components. The first is a <b>Static Mesh</b> (name it Cube) and the second is a <b>Box Collision</b> (name it KillVolume). Attach the Collision to the SceneRoot by clicking and dragging it onto the Root.

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

On the Static Mesh, select one of the default Cube meshes that Unreal provides. You will need to have <b>Show Engine Content</b> enabled to see these.

<img src="images/2021-11-18 10_10_19-.png" />

Scroll down to the <b>Collision</b> section and look at the <b>Collision Preset</b>. Make sure that it is set to <b>OverlapAllDynamic</b>. 

<img src="images/2021-11-23 09_45_16-.png" />

Before we continue, open up the Mesh you selected by double-clicking it. Under <b>Collision</b>, select <b>Remove Collision</b>, as we’ll be using the Box Collider that we made instead.

<img src="images/2021-11-18 11_21_28-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`ITA`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

On the Collision Volume you just created, make sure that the size matches that of the Cube mesh. With the Box Collision selected, look at the Shape section. For mine I had to set the Box Extents to 50 on all sides. When done, compile this Blueprint and return to the scene.

<img src="images/2021-11-23 10_30_23-KillVolume.odt - LibreOffice Writer.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`ITA`| :small_orange_diamond:

Drop a copy of the BP_KillVolume into the scene. Scale it to a decent size (at least tall enough to encompass the player)

<img src="images/2021-11-18 09_42_41-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`ITA`| :small_orange_diamond: :small_blue_diamond:

Go to your Materials folder and create a new Material called <b>M_VolumeVisualizer</b>. First, let’s make sure our Material is setup to be <b>Translucent</b>. Click the Result Node of the Material and set the Blend Mode to <b>Translucent</b>.

<img src="images/2021-11-18 09_48_42-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

On the graph add a <b>Constant3Vector</b> and connect it to the Base Color. I set it to a bright red to make it easy to see. Also add a <b>Constant</b> and connect it to Opacity. I set its value to be 0.4. Compile and save it.

<img src="images/2021-11-18 10_00_18-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`ITA`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We’re done with the material, so now we can attach it to the Blueprint. Click on the Cube (the Static Mesh) and go to the Material section. Simply type in the name of your visualizer material to add it to the Cube. Compile this Blueprint.

<img src="images/2021-11-18 10_12_30-UE4LevelDesignExtras - Unreal Editor.png" />

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>
___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Kill Volume Event Graph">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [home](../README.md#level-design-kill-volumes) | [next](../kill-volume-event-graph/README.md#kill-volume-event-graph)|
|---|---|
