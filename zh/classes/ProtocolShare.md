## `ProtocolShare` Class

Extends [`PluginProtocol`](PluginProtocol.md)


Module: [anysdk](../modules/anysdk.md)




分享系统协议接口

### Index



##### Methods

  - [`share`](#share) 分享
  - [`setListener`](#setlistener) 设置分享系统的监听
  - [`getListener`](#getlistener) 获取分享系统的监听
  - [`isFunctionSupported`](#isfunctionsupported) 判断函数是否支持
  - [`getPluginName`](#getpluginname) 获取插件名称
  - [`getPluginVersion`](#getpluginversion) 获取插件版本
  - [`getSDKVersion`](#getsdkversion) 获取 SDK 版本
  - [`callFuncWithParam`](#callfuncwithparam) 反射调用带参数的void方法
  - [`callStringFuncWithParam`](#callstringfuncwithparam) 反射调用带参数的 String 方法
  - [`callIntFuncWithParam`](#callintfuncwithparam) 反射调用带参数的 Int 方法
  - [`callBoolFuncWithParam`](#callboolfuncwithparam) 反射调用带参数的 boolean 方法
  - [`callFloatFuncWithParam`](#callfloatfuncwithparam) 反射调用带参数的 float 方法



### Details




<!-- Method Block -->
#### Methods


##### share

分享

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:1048](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L1048) |

###### Parameters
- info <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> Type: map


##### setListener

设置分享系统的监听

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:1058](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L1058) |

###### Parameters
- listener <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 
- target <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> 


##### getListener

获取分享系统的监听

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:1070](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L1070) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 



##### isFunctionSupported

判断函数是否支持

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:327](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L327) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">boolean</a> 

###### Parameters
- functionName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 


##### getPluginName

获取插件名称

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:341](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L341) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 



##### getPluginVersion

获取插件版本

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:353](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L353) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 



##### getSDKVersion

获取 SDK 版本

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:365](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L365) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 



##### callFuncWithParam

反射调用带参数的void方法

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:377](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L377) |

###### Parameters
- funName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- args <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> &#124; anysdk.PluginParam optional arguments


##### callStringFuncWithParam

反射调用带参数的 String 方法

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:390](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L390) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 

###### Parameters
- funName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- args <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> &#124; anysdk.PluginParam optional arguments


##### callIntFuncWithParam

反射调用带参数的 Int 方法

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:405](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L405) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 

###### Parameters
- funName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- args <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> &#124; anysdk.PluginParam optional arguments


##### callBoolFuncWithParam

反射调用带参数的 boolean 方法

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:420](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L420) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Boolean" class="crosslink external" target="_blank">boolean</a> 

###### Parameters
- funName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- args <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> &#124; anysdk.PluginParam optional arguments


##### callFloatFuncWithParam

反射调用带参数的 float 方法

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js:435](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/extensions/anysdk/jsb_anysdk.js#L435) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 

###### Parameters
- funName <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 
- args <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> &#124; anysdk.PluginParam optional arguments


