## Create simple logic

Here is an illustrated example of simple logic creation for two actors.

Name them **BP_Generator** and **BP_Light_Bulb**

![](../images/examples/example_1/1.png)

Create new **LogicalStateDataAsset** and name it **DA_States_Default**

![](../images/examples/example_1/2.png)

Add two new lines to the data asset: **Activated** and **Deactivated**

![](../images/examples/example_1/3.png)

Add **Logical State** and **Logical Signal Generator** components to **BP_Generator**

![](../images/examples/example_1/4.png)

In the **Logical State** component settings, select **DA_States_Default** as **Parent States** and **Deactivated** as **Initialization State**

![](../images/examples/example_1/5.png)

In the **Logical Signal Generator** component settings, add a new **Generator Signal**.

In the signal settings, add a new element to the **Activation States** array - **Activated** (this is the state that allows signals to generate).

Add a new item to the **Signals** array and select your signal type tag and signal channel tag.

![](../images/examples/example_1/6.png)

Add **Point Light**, **Logical State** and **Logical Signal Receiver** components to **BP_Light_Bulb**

![](../images/examples/example_1/7.png)

In the **Logical State** component settings, select **DA_States_Default** as **Parent States** and **Deactivated** as **Initialization State**

![](../images/examples/example_1/8.png)

In the **Logical Signal Receiver** component settings, add new **Signals to Receive**.

In the signal settings, set **Activated** to **State on Signal** and **Deactivated** to **State on Lost Signal**.

Add a new item to the signals array and select the same signal type tag and signal channel tag.

![](../images/examples/example_1/9.png)

Add a new event to the **Logical State** component **OnStateChanged**

![](../images/examples/example_1/10.png)

Add a switch node

![](../images/examples/example_1/11.png)

In the switch node settings, click the **Add All States** button

![](../images/examples/example_1/12.png)

Add **Set Visibility** for **Point Light**

![](../images/examples/example_1/13.png)

Add our two actors to the map and switch the editor to **Logical Chains mode**.

![](../images/examples/example_1/14.png)

![](../images/examples/example_1/15.png)

![](../images/examples/example_1/16.png)

To test it, let's add some code to the level blueprint (If you have an interactive system in your project, you can use it)

![](../images/examples/example_1/17.png)

Now we can check

![](../gifs/Gif1.gif)

Now let's try adding a switch and extra bulbs to our circuit

Create new a actor and name it **BP_Switch**

Add **Logical State** and **Logical Signal Generator** components

![](../images/examples/example_1/18.png)

**Logical State Component** settings

![](../images/examples/example_1/19.png)

**Logical Signal Generator** settings

![](../images/examples/example_1/20.png)

It's the same **BP_Generator** that creates a different signal, but in it, we'll add a visual display of the toggle. Select **OnStateChanged** in the **State component**

![](../images/examples/example_1/21.png)

Add the desired logic. In my example I switch the color of the cone.

![](../images/examples/example_1/22.png)

In the bulb settings on the scene change the conditions and add a new signal to turn it on. 

![](../images/examples/example_1/23.png)

Add **BP_Switch** to the scene and code to check work in level blueprint

![](../images/examples/example_1/24.png)

![](../gifs/Gif2.gif)

We can also create additional bulbs and configure their own unique behavior.
In the example below the top bulbs are connected only to the generator and the right one is connected to the switch and the generator.

![](../gifs/Gif3.gif)
