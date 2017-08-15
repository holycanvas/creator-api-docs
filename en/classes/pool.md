## `Pool` Class



Module: [cc](../modules/cc.md)
Parent Module: [js](../modules/js.md)




A fixed-length object pool designed for general type.<br>
The implementation of this object pool is very simple,
it can helps you to improve your game performance for objects which need frequent release and recreate operations<br/>

### Index

##### Properties

  - [`count`](#count) `Number` The current number of available objects, the default is 0, it will gradually increase with the recycle of the object,
the maximum will not exceed the size specified when the constructor is called.



##### Methods

  - [`constructor`](#constructor) Constructor for creating an object pool for the specific object type.
You can pass a callback argument for process the cleanup logic when the object is recycled.
  - [`get`](#get) Get and initialize an object from pool. This method defaults to null and requires the user to implement it.
  - [`_get`](#get) Get an object from pool, if no available object in the pool, null will be returned.
  - [`put`](#put) Put an object into the pool.
  - [`resize`](#resize) Resize the pool.



### Details


#### Properties


##### count

> The current number of available objects, the default is 0, it will gradually increase with the recycle of the object,
the maximum will not exceed the size specified when the constructor is called.

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js:877](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js#L877) |






<!-- Method Block -->
#### Methods


##### constructor

Constructor for creating an object pool for the specific object type.
You can pass a callback argument for process the cleanup logic when the object is recycled.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js:842](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js#L842) |

###### Parameters
- cleanupFunc <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> the callback method used to process the cleanup logic when the object is recycled.
	- obj <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 
- size <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> initializes the length of the array


##### get

Get and initialize an object from pool. This method defaults to null and requires the user to implement it.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js:867](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js#L867) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 

###### Parameters
- params Any parameters to used to initialize the object


##### _get

Get an object from pool, if no available object in the pool, null will be returned.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js:887](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js#L887) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> &#124; Null 



##### put

Put an object into the pool.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js:905](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js#L905) |



##### resize

Resize the pool.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js:921](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/js.js#L921) |



