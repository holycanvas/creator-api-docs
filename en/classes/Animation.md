## `Animation` Class

Extends [`Component`](Component.md)


Module: [cc](../modules/cc.md)




The animation component is used to play back animations.

Animation provide several events to register：
 - play : Emit when begin playing animation
 - stop : Emit when stop playing animation
 - pause : Emit when pause animation
 - resume : Emit when resume animation
 - lastframe : If animation repeat count is larger than 1, emit when animation play to the last frame
 - finished : Emit when finish playing animation

### Index

##### Properties

  - [`defaultClip`](#defaultclip) `AnimationClip` Animation will play the default clip when start game.
  - [`currentClip`](#currentclip) `AnimationClip` Current played clip.
  - [`_clips`](#clips) `AnimationClip[]` All the clips used in this animation.
  - [`playOnLoad`](#playonload) `Boolean` Whether the animation should auto play the default clip when start game.
  - [`__eventTargets`](#eventtargets) `Array` Register all related EventTargets,
all event callbacks will be removed in _onPreDestroy
  - [`node`](#node) `Node` The node this component is attached to. A component is always attached to a node.
  - [`uuid`](#uuid) `String` The uuid for editor.
  - [`_enabled`](#enabled) `Boolean` 
  - [`enabled`](#enabled) `Boolean` indicates whether this component is enabled or not.
  - [`enabledInHierarchy`](#enabledinhierarchy) `Boolean` indicates whether this component is enabled and its node is also active in the hierarchy.
  - [`_isOnLoadCalled`](#isonloadcalled) `Number` Returns a value which used to indicate the onLoad get called or not.
  - [`_name`](#name) `String` 
  - [`_objFlags`](#objflags) `Number` 
  - [`name`](#name) `String` The name of the object.
  - [`isValid`](#isvalid) `Boolean` Indicates whether the object is not yet destroyed.



##### Methods

  - [`getClips`](#getclips) Get all the clips used in this animation.
  - [`play`](#play) Plays an animation and stop other animations.
  - [`playAdditive`](#playadditive) Plays an additive animation, it will not stop other animations.
If there are other animations playing, then will play several animations at the same time.
  - [`stop`](#stop) Stops an animation named name. If no name is supplied then stops all playing animations that were started with this Animation. <br/>
Stopping an animation also Rewinds it to the Start.
  - [`pause`](#pause) Pauses an animation named name. If no name is supplied then pauses all playing animations that were started with this Animation.
  - [`resume`](#resume) Resumes an animation named name. If no name is supplied then resumes all paused animations that were started with this Animation.
  - [`setCurrentTime`](#setcurrenttime) Make an animation named name go to the specified time. If no name is supplied then make all animations go to the specified time.
  - [`getAnimationState`](#getanimationstate) Returns the animation state named name. If no animation with the specified name, the function will return null.
  - [`addClip`](#addclip) Adds a clip to the animation with name newName. If a clip with that name already exists it will be replaced with the new clip.
  - [`removeClip`](#removeclip) Remove clip from the animation list. This will remove the clip and any animation states based on it.
If there are animation states depand on the clip are playing or clip is defaultClip, it will not delete the clip.
But if force is true, then will always remove the clip and any animation states based on it. If clip is defaultClip, defaultClip will be reset to null
  - [`sample`](#sample) Samples animations at the current state.<br/>
This is useful when you explicitly want to set up some animation state, and sample it once.
  - [`on`](#on) Register animation event callback.
The event arguments will provide the AnimationState which emit the event.
When play an animation, will auto register the event callback to the AnimationState, and unregister the event callback from the AnimationState when animation stopped.
  - [`off`](#off) Unregister animation event callback.
  - [`update`](#update) Update is called every frame, if the Component is enabled.
  - [`lateUpdate`](#lateupdate) LateUpdate is called every frame, if the Component is enabled.
  - [`__preload`](#preload) `__preload` is called before every onLoad.
It is used to initialize the builtin components internally,
to avoid checking whether onLoad is called before every public method calls.
This method should be removed if script priority is supported.
  - [`onLoad`](#onload) When attaching to an active node or its node first activated.
onLoad is always called before any start functions, this allows you to order initialization of scripts.
  - [`start`](#start) Called before all scripts' update if the Component is enabled the first time.
Usually used to initialize some logic which need to be called after all components' `onload` methods called.
  - [`onEnable`](#onenable) Called when this component becomes enabled and its node is active.
  - [`onDisable`](#ondisable) Called when this component becomes disabled or its node becomes inactive.
  - [`onDestroy`](#ondestroy) Called when this component will be destroyed.
  - [`onFocusInEditor`](#onfocusineditor) 
  - [`onLostFocusInEditor`](#onlostfocusineditor) 
  - [`resetInEditor`](#resetineditor) Called to initialize the component or node’s properties when adding the component the first time or when the Reset command is used. This function is only called in editor.
  - [`addComponent`](#addcomponent) Adds a component class to the node. You can also add component to node by passing in the name of the script.
  - [`getComponent`](#getcomponent) Returns the component of supplied type if the node has one attached, null if it doesn't.<br/>
You can also get component in the node by passing in the name of the script.
  - [`getComponents`](#getcomponents) Returns all components of supplied Type in the node.
  - [`getComponentInChildren`](#getcomponentinchildren) Returns the component of supplied type in any of its children using depth first search.
  - [`getComponentsInChildren`](#getcomponentsinchildren) Returns the components of supplied type in self or any of its children using depth first search.
  - [`_getLocalBounds`](#getlocalbounds) If the component's bounding box is different from the node's, you can implement this method to supply
a custom axis aligned bounding box (AABB), so the editor's scene view can perform hit test properly.
  - [`onRestore`](#onrestore) onRestore is called after the user clicks the Reset item in the Inspector's context menu or performs
an undo operation on this component.<br/>
<br/>
If the component contains the "internal state", short for "temporary member variables which not included<br/>
in its CCClass properties", then you may need to implement this function.<br/>
<br/>
The editor will call the getset accessors of your component to record/restore the component's state<br/>
for undo/redo operation. However, in extreme cases, it may not works well. Then you should implement<br/>
this function to manually synchronize your component's "internal states" with its public properties.<br/>
Once you implement this function, all the getset accessors of your component will not be called when<br/>
the user performs an undo/redo operation. Which means that only the properties with default value<br/>
will be recorded or restored by editor.<br/>
<br/>
Similarly, the editor may failed to reset your component correctly in extreme cases. Then if you need<br/>
to support the reset menu, you should manually synchronize your component's "internal states" with its<br/>
properties in this function. Once you implement this function, all the getset accessors of your component<br/>
will not be called during reset operation. Which means that only the properties with default value<br/>
will be reset by editor.

This function is only called in editor mode.
  - [`schedule`](#schedule) Schedules a custom selector.<br/>
If the selector is already scheduled, then the interval parameter will be updated without scheduling it again.
  - [`scheduleOnce`](#scheduleonce) Schedules a callback function that runs only once, with a delay of 0 or larger.
  - [`unschedule`](#unschedule) Unschedules a custom callback function.
  - [`unscheduleAllCallbacks`](#unscheduleallcallbacks) unschedule all scheduled callback functions: custom callback functions, and the 'update' callback function.<br/>
Actions are not affected by this method.
  - [`targetOff`](#targetoff) Removes all callbacks previously registered with the same target (passed as parameter).
This is not for removing all listeners in the current event target,
and this is not for removing all listeners the target parameter have registered.
It's only for removing all listeners (callback and target couple) registered on the current event target by the target parameter.
  - [`once`](#once) Register an callback of a specific event type on the EventTarget,
the callback will remove itself after the first time it is triggered.
  - [`dispatchEvent`](#dispatchevent) Dispatches an event into the event flow.
The event target is the EventTarget object upon which the dispatchEvent() method is called.
  - [`emit`](#emit) Send an event to this object directly, this method will not propagate the event to any other objects.
The event will be created from the supplied message, you can get the "detail" argument from event.detail.
  - [`destroy`](#destroy) Destroy this Object, and release all its own references to other objects.<br/>
Actual object destruction will delayed until before rendering.
<br/>
After destroy, this CCObject is not usable any more.
You can use cc.isValid(obj) to check whether the object is destroyed before accessing it.
  - [`_destruct`](#destruct) Clear all references in the instance.

NOTE: this method will not clear the getter or setter functions which defined in the instance of CCObject.
      You can override the _destruct method if you need, for example:
      _destruct: function () {
          for (var key in this) {
              if (this.hasOwnProperty(key)) {
                  switch (typeof this[key]) {
                      case 'string':
                          this[key] = '';
                          break;
                      case 'object':
                      case 'function':
                          this[key] = null;
                          break;
              }
          }
      }
  - [`_onPreDestroy`](#onpredestroy) Called before the object being destroyed.
  - [`_serialize`](#serialize) The customized serialization for this object. (Editor Only)
  - [`_deserialize`](#deserialize) Init this object from the custom serialized data.



### Details


#### Properties


##### defaultClip

> Animation will play the default clip when start game.

| meta | description |
|------|-------------|
| Type | <a href="../classes/AnimationClip.html" class="crosslink">AnimationClip</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:95](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L95) |



##### currentClip

> Current played clip.

| meta | description |
|------|-------------|
| Type | <a href="../classes/AnimationClip.html" class="crosslink">AnimationClip</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:130](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L130) |



##### _clips

> All the clips used in this animation.

| meta | description |
|------|-------------|
| Type | <a href="../classes/AnimationClip.html" class="crosslink">AnimationClip[]</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:147](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L147) |



##### playOnLoad

> Whether the animation should auto play the default clip when start game.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:161](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L161) |



##### __eventTargets

> Register all related EventTargets,
all event callbacks will be removed in _onPreDestroy

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Array" class="crosslink external" target="_blank">Array</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:61](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L61) |



##### node

> The node this component is attached to. A component is always attached to a node.

| meta | description |
|------|-------------|
| Type | <a href="../classes/Node.html" class="crosslink">Node</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:75](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L75) |

##### Examples

```js
cc.log(comp.node);
```


##### uuid

> The uuid for editor.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:111](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L111) |

##### Examples

```js
cc.log(comp.uuid);
```


##### _enabled

> 

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:159](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L159) |



##### enabled

> indicates whether this component is enabled or not.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:166](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L166) |

##### Examples

```js
comp.enabled = true;
cc.log(comp.enabled);
```


##### enabledInHierarchy

> indicates whether this component is enabled and its node is also active in the hierarchy.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:197](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L197) |

##### Examples

```js
cc.log(comp.enabledInHierarchy);
```


##### _isOnLoadCalled

> Returns a value which used to indicate the onLoad get called or not.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:213](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L213) |

##### Examples

```js
cc.log(this._isOnLoadCalled > 0);
```


##### _name

> 

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:50](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L50) |



##### _objFlags

> 

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:57](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L57) |



##### name

> The name of the object.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:208](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L208) |

##### Examples

```js
obj.name = "New Obj";
```


##### isValid

> Indicates whether the object is not yet destroyed.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:225](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L225) |

##### Examples

```js
cc.log(obj.isValid);
```





<!-- Method Block -->
#### Methods


##### getClips

Get all the clips used in this animation.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:201](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L201) |
| Return 		 | <a href="../classes/AnimationClip.html" class="crosslink">AnimationClip[]</a> 



##### play

Plays an animation and stop other animations.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:211](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L211) |
| Return 		 | <a href="../classes/AnimationState.html" class="crosslink">AnimationState</a> 

###### Parameters
- name <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> The name of animation to play. If no name is supplied then the default animation will be played.
- startTime <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> play an animation from startTime

##### Example

```js
var animCtrl = this.node.getComponent(cc.Animation);
animCtrl.play("linear");
```

##### playAdditive

Plays an additive animation, it will not stop other animations.
If there are other animations playing, then will play several animations at the same time.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:228](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L228) |
| Return 		 | <a href="../classes/AnimationState.html" class="crosslink">AnimationState</a> 

###### Parameters
- name <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> The name of animation to play. If no name is supplied then the default animation will be played.
- startTime <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> play an animation from startTime

##### Example

```js
// linear_1 and linear_2 at the same time playing.
var animCtrl = this.node.getComponent(cc.Animation);
animCtrl.playAdditive("linear_1");
animCtrl.playAdditive("linear_2");
```

##### stop

Stops an animation named name. If no name is supplied then stops all playing animations that were started with this Animation. <br/>
Stopping an animation also Rewinds it to the Start.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:269](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L269) |

###### Parameters
- name <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> The animation to stop, if not supplied then stops all playing animations.


##### pause

Pauses an animation named name. If no name is supplied then pauses all playing animations that were started with this Animation.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:291](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L291) |

###### Parameters
- name <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> The animation to pauses, if not supplied then pauses all playing animations.


##### resume

Resumes an animation named name. If no name is supplied then resumes all paused animations that were started with this Animation.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:312](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L312) |

###### Parameters
- name <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> The animation to resumes, if not supplied then resumes all paused animations.


##### setCurrentTime

Make an animation named name go to the specified time. If no name is supplied then make all animations go to the specified time.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:333](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L333) |

###### Parameters
- time <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> The time to go to
- name <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> Specified animation name, if not supplied then make all animations go to the time.


##### getAnimationState

Returns the animation state named name. If no animation with the specified name, the function will return null.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:353](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L353) |
| Return 		 | <a href="../classes/AnimationState.html" class="crosslink">AnimationState</a> 

###### Parameters
- name <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 


##### addClip

Adds a clip to the animation with name newName. If a clip with that name already exists it will be replaced with the new clip.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:382](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L382) |
| Return 		 | <a href="../classes/AnimationState.html" class="crosslink">AnimationState</a> 

###### Parameters
- clip <a href="../classes/AnimationClip.html" class="crosslink">AnimationClip</a> the clip to add
- newName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 


##### removeClip

Remove clip from the animation list. This will remove the clip and any animation states based on it.
If there are animation states depand on the clip are playing or clip is defaultClip, it will not delete the clip.
But if force is true, then will always remove the clip and any animation states based on it. If clip is defaultClip, defaultClip will be reset to null

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:423](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L423) |

###### Parameters
- clip <a href="../classes/AnimationClip.html" class="crosslink">AnimationClip</a> 
- force <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> If force is true, then will always remove the clip and any animation states based on it.


##### sample

Samples animations at the current state.<br/>
This is useful when you explicitly want to set up some animation state, and sample it once.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:477](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L477) |

###### Parameters
- name <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 


##### on

Register animation event callback.
The event arguments will provide the AnimationState which emit the event.
When play an animation, will auto register the event callback to the AnimationState, and unregister the event callback from the AnimationState when animation stopped.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:500](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L500) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 

###### Parameters
- type <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> A string representing the event type to listen for.
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> The callback that will be invoked when the event is dispatched.
                             The callback is ignored if it is a duplicate (the callbacks are unique).
	- event <a href="../classes/Event.html" class="crosslink">Event</a> event
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The target to invoke the callback, can be null
- useCapture <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> When set to true, the capture argument prevents callback
                             from being invoked when the event's eventPhase attribute value is BUBBLING_PHASE.
                             When false, callback will NOT be invoked when event's eventPhase attribute value is CAPTURING_PHASE.
                             Either way, callback will be invoked when event's eventPhase attribute value is AT_TARGET.

##### Example

```js
onPlay: function (event) {
    var state = event.detail;    // state instanceof cc.AnimationState
    var type = event.type;       // type === 'play';
}

// register event to all animation
animation.on('play', this.onPlay, this);
```

##### off

Unregister animation event callback.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js:554](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCAnimation.js#L554) |

###### Parameters
- type <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> A string representing the event type being removed.
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> The callback to remove.
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The target to invoke the callback, if it's not given, only callback without target will be removed
- useCapture <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> Specifies whether the callback being removed was registered as a capturing callback or not.
                             If not specified, useCapture defaults to false. If a callback was registered twice,
                             one with capture and one without, each must be removed separately. Removal of a capturing callback
                             does not affect a non-capturing version of the same listener, and vice versa.

##### Example

```js
// unregister event to all animation
animation.off('play', this.onPlay, this);
```

##### update

Update is called every frame, if the Component is enabled.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:234](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L234) |

###### Parameters
- dt <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> the delta time in seconds it took to complete the last frame


##### lateUpdate

LateUpdate is called every frame, if the Component is enabled.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:243](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L243) |



##### __preload

`__preload` is called before every onLoad.
It is used to initialize the builtin components internally,
to avoid checking whether onLoad is called before every public method calls.
This method should be removed if script priority is supported.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:251](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L251) |



##### onLoad

When attaching to an active node or its node first activated.
onLoad is always called before any start functions, this allows you to order initialization of scripts.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:262](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L262) |



##### start

Called before all scripts' update if the Component is enabled the first time.
Usually used to initialize some logic which need to be called after all components' `onload` methods called.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:273](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L273) |



##### onEnable

Called when this component becomes enabled and its node is active.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:284](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L284) |



##### onDisable

Called when this component becomes disabled or its node becomes inactive.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:292](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L292) |



##### onDestroy

Called when this component will be destroyed.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:300](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L300) |



##### onFocusInEditor



| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:308](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L308) |



##### onLostFocusInEditor



| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:313](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L313) |



##### resetInEditor

Called to initialize the component or node’s properties when adding the component the first time or when the Reset command is used. This function is only called in editor.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:318](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L318) |



##### addComponent

Adds a component class to the node. You can also add component to node by passing in the name of the script.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:328](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L328) |
| Return 		 | <a href="../classes/Component.html" class="crosslink">Component</a> 

###### Parameters
- typeOrClassName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> &#124; <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> the constructor or the class name of the component to add

##### Example

```js
var sprite = node.addComponent(cc.Sprite);
var test = node.addComponent("Test");
```

##### getComponent

Returns the component of supplied type if the node has one attached, null if it doesn't.<br/>
You can also get component in the node by passing in the name of the script.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:346](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L346) |
| Return 		 | <a href="../classes/Component.html" class="crosslink">Component</a> 

###### Parameters
- typeOrClassName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> &#124; <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 

##### Example

```js
// get sprite component.
var sprite = node.getComponent(cc.Sprite);
// get custom test calss.
var test = node.getComponent("Test");
```

##### getComponents

Returns all components of supplied Type in the node.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:370](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L370) |
| Return 		 | <a href="../classes/Component.html" class="crosslink">Component[]</a> 

###### Parameters
- typeOrClassName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> &#124; <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 

##### Example

```js
var sprites = node.getComponents(cc.Sprite);
var tests = node.getComponents("Test");
```

##### getComponentInChildren

Returns the component of supplied type in any of its children using depth first search.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:388](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L388) |
| Return 		 | <a href="../classes/Component.html" class="crosslink">Component</a> 

###### Parameters
- typeOrClassName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> &#124; <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 

##### Example

```js
var sprite = node.getComponentInChildren(cc.Sprite);
var Test = node.getComponentInChildren("Test");
```

##### getComponentsInChildren

Returns the components of supplied type in self or any of its children using depth first search.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:406](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L406) |
| Return 		 | <a href="../classes/Component.html" class="crosslink">Component[]</a> 

###### Parameters
- typeOrClassName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> &#124; <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 

##### Example

```js
var sprites = node.getComponentsInChildren(cc.Sprite);
var tests = node.getComponentsInChildren("Test");
```

##### _getLocalBounds

If the component's bounding box is different from the node's, you can implement this method to supply
a custom axis aligned bounding box (AABB), so the editor's scene view can perform hit test properly.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:426](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L426) |

###### Parameters
- out_rect <a href="../classes/Rect.html" class="crosslink">Rect</a> the Rect to receive the bounding box


##### onRestore

onRestore is called after the user clicks the Reset item in the Inspector's context menu or performs
an undo operation on this component.<br/>
<br/>
If the component contains the "internal state", short for "temporary member variables which not included<br/>
in its CCClass properties", then you may need to implement this function.<br/>
<br/>
The editor will call the getset accessors of your component to record/restore the component's state<br/>
for undo/redo operation. However, in extreme cases, it may not works well. Then you should implement<br/>
this function to manually synchronize your component's "internal states" with its public properties.<br/>
Once you implement this function, all the getset accessors of your component will not be called when<br/>
the user performs an undo/redo operation. Which means that only the properties with default value<br/>
will be recorded or restored by editor.<br/>
<br/>
Similarly, the editor may failed to reset your component correctly in extreme cases. Then if you need<br/>
to support the reset menu, you should manually synchronize your component's "internal states" with its<br/>
properties in this function. Once you implement this function, all the getset accessors of your component<br/>
will not be called during reset operation. Which means that only the properties with default value<br/>
will be reset by editor.

This function is only called in editor mode.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:439](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L439) |



##### schedule

Schedules a custom selector.<br/>
If the selector is already scheduled, then the interval parameter will be updated without scheduling it again.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:541](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L541) |

###### Parameters
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">function</a> The callback function
- interval <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> Tick interval in seconds. 0 means tick every frame. If interval = 0, it's recommended to use scheduleUpdate() instead.
- repeat <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> The selector will be executed (repeat + 1) times, you can use kCCRepeatForever for tick infinitely.
- delay <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> The amount of time that the first tick will wait before execution.

##### Example

```js
var timeCallback = function (dt) {
  cc.log("time: " + dt);
}
this.schedule(timeCallback, 1);
```

##### scheduleOnce

Schedules a callback function that runs only once, with a delay of 0 or larger.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:570](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L570) |

###### Parameters
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">function</a> A function wrapped as a selector
- delay <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> The amount of time that the first tick will wait before execution.

##### Example

```js
var timeCallback = function (dt) {
  cc.log("time: " + dt);
}
this.scheduleOnce(timeCallback, 2);
```

##### unschedule

Unschedules a custom callback function.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:587](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L587) |

###### Parameters
- callback_fn <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">function</a> A function wrapped as a selector

##### Example

```js
this.unschedule(_callback);
```

##### unscheduleAllCallbacks

unschedule all scheduled callback functions: custom callback functions, and the 'update' callback function.<br/>
Actions are not affected by this method.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js:603](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/components/CCComponent.js#L603) |


##### Example

```js
this.unscheduleAllCallbacks();
```

##### targetOff

Removes all callbacks previously registered with the same target (passed as parameter).
This is not for removing all listeners in the current event target,
and this is not for removing all listeners the target parameter have registered.
It's only for removing all listeners (callback and target couple) registered on the current event target by the target parameter.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/event/event-target.js:257](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/event/event-target.js#L257) |

###### Parameters
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The target to be searched for all related listeners


##### once

Register an callback of a specific event type on the EventTarget,
the callback will remove itself after the first time it is triggered.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/event/event-target.js:277](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/event/event-target.js#L277) |

###### Parameters
- type <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> A string representing the event type to listen for.
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> The callback that will be invoked when the event is dispatched.
                             The callback is ignored if it is a duplicate (the callbacks are unique).
	- event <a href="../classes/Event.html" class="crosslink">Event</a> event
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The target to invoke the callback, can be null
- useCapture <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> When set to true, the capture argument prevents callback
                             from being invoked when the event's eventPhase attribute value is BUBBLING_PHASE.
                             When false, callback will NOT be invoked when event's eventPhase attribute value is CAPTURING_PHASE.
                             Either way, callback will be invoked when event's eventPhase attribute value is AT_TARGET.

##### Example

```js
node.once(cc.Node.EventType.TOUCH_END, function (event) {
    cc.log("this is callback");
}, node);
```

##### dispatchEvent

Dispatches an event into the event flow.
The event target is the EventTarget object upon which the dispatchEvent() method is called.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/event/event-target.js:311](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/event/event-target.js#L311) |

###### Parameters
- event <a href="../classes/Event.html" class="crosslink">Event</a> The Event object that is dispatched into the event flow


##### emit

Send an event to this object directly, this method will not propagate the event to any other objects.
The event will be created from the supplied message, you can get the "detail" argument from event.detail.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/event/event-target.js:325](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/event/event-target.js#L325) |

###### Parameters
- message <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> the message to send
- detail Any whatever argument the message needs


##### destroy

Destroy this Object, and release all its own references to other objects.<br/>
Actual object destruction will delayed until before rendering.
<br/>
After destroy, this CCObject is not usable any more.
You can use cc.isValid(obj) to check whether the object is destroyed before accessing it.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:246](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L246) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 


##### Example

```js
obj.destroy();
```

##### _destruct

Clear all references in the instance.

NOTE: this method will not clear the getter or setter functions which defined in the instance of CCObject.
      You can override the _destruct method if you need, for example:
      _destruct: function () {
          for (var key in this) {
              if (this.hasOwnProperty(key)) {
                  switch (typeof this[key]) {
                      case 'string':
                          this[key] = '';
                          break;
                      case 'object':
                      case 'function':
                          this[key] = null;
                          break;
              }
          }
      }

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:366](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L366) |



##### _onPreDestroy

Called before the object being destroyed.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:399](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L399) |



##### _serialize

The customized serialization for this object. (Editor Only)

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:424](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L424) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">object</a> 

###### Parameters
- exporting <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 


##### _deserialize

Init this object from the custom serialized data.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:434](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L434) |

###### Parameters
- data <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> the serialized json data
- ctx _Deserializer 


