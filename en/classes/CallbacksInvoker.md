## `CallbacksInvoker` Class

Extends [`_CallbacksHandler`](_CallbacksHandler.md)


Module: [_decorator](../modules/_decorator.md)
Parent Module: [cc](../modules/cc.md)




The callbacks invoker to handle and invoke callbacks by key.

### Index



##### Methods

  - [`invoke`](#invoke) 
  - [`invokeAndRemove`](#invokeandremove) 
  - [`bindKey`](#bindkey) 
  - [`add`](#add) 
  - [`has`](#has) Check if the specified key has any registered callback. If a callback is also specified,
it will only return true if the callback is registered.
  - [`removeAll`](#removeall) Removes all callbacks registered in a certain event type or all callbacks registered with a certain target
  - [`remove`](#remove) 



### Details




<!-- Method Block -->
#### Methods


##### invoke



| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js:242](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js#L242) |

###### Parameters
- key <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- p1 Any 
- p2 Any 
- p3 Any 
- p4 Any 
- p5 Any 


##### invokeAndRemove



| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js:281](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js#L281) |

###### Parameters
- key <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- p1 Any 
- p2 Any 
- p3 Any 
- p4 Any 
- p5 Any 


##### bindKey



| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js:319](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js#L319) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 

###### Parameters
- key <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- remove <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> remove callbacks after invoked


##### add



| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js:71](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js#L71) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 

###### Parameters
- key <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> can be null


##### has

Check if the specified key has any registered callback. If a callback is also specified,
it will only return true if the callback is registered.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js:104](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js#L104) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 

###### Parameters
- key <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 


##### removeAll

Removes all callbacks registered in a certain event type or all callbacks registered with a certain target

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js:155](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js#L155) |

###### Parameters
- key <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> &#124; <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> The event key to be removed or the target to be removed


##### remove



| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js:188](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/callbacks-invoker.js#L188) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">Boolean</a> 

###### Parameters
- key <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a>  
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a>  
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a>  


