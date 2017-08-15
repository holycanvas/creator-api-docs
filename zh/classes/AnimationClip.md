## `AnimationClip` Class

Extends [`Asset`](Asset.md)


Module: [cc](../modules/cc.md)




动画剪辑，用于存储动画数据。

### Index

##### Properties

  - [`duration`](#duration) `Number` 动画的持续时间。
  - [`sample`](#sample) `Number` 动画的帧速率。
  - [`speed`](#speed) `Number` 动画的播放速度。
  - [`wrapMode`](#wrapmode) `WrapMode` 动画的循环模式。
  - [`curveData`](#curvedata) `Object` 曲线数据。
  - [`events`](#events) `Object[]` 事件数据。
  - [`rawUrl`](#rawurl) `String` 返回该资源的原始文件的 URL，如果不支持 RAW 文件，它将返回一个空字符串。
  - [`rawUrls`](#rawurls) `String[]` 返回该资源的原文件的 URL 数组，如果不支持 RAW 文件，它将返回一个空数组。
  - [`_rawFiles`](#rawfiles) `String[]` 在 lite 版的 Fireball 里，raw asset 并不仅仅是在 properties 里声明了 rawType 才有，
而是每个 asset 都能指定自己的 raw file url。这些 url 就存在 _rawFiles 字段中。
AssetLibrary 并不会帮你加载这些 url，除非你声明了 rawType。
在 Creator 里，_rawFiles 保留了下来，为了复用 cocos 引擎原有实现，直接用 _rawFiles 来加载 Asset 在 import 之前的源文件。
  - [`_uuid`](#uuid) `String` 
  - [`_name`](#name) `String` 
  - [`_objFlags`](#objflags) `Number` 
  - [`name`](#name) `String` 该对象的名称。
  - [`isValid`](#isvalid) `Boolean` 表示该对象是否可用（被销毁后将不可用）。



##### Methods

  - [`createWithSpriteFrames`](#createwithspriteframes) 使用一组序列帧图片来创建动画剪辑
  - [`serialize`](#serialize) 应 AssetDB 要求提供这个方法
  - [`createNode`](#createnode) 使用该资源在场景中创建一个新节点。<br/>
如果这类资源没有相应的节点类型，该方法应该是空的。
  - [`_setRawFiles`](#setrawfiles) Set raw file names for this asset.
  - [`_preloadRawFiles`](#preloadrawfiles) Preload raw files when loading scene.
  - [`destroy`](#destroy) 销毁该对象，并释放所有它对其它对象的引用。<br/>
销毁后，CCObject 不再可用。您可以在访问对象之前使用 cc.isValid(obj) 来检查对象是否已被销毁。
实际销毁操作会延迟到当前帧渲染前执行。
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


##### duration

> 动画的持续时间。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js:21](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js#L21) |



##### sample

> 动画的帧速率。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js:31](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js#L31) |



##### speed

> 动画的播放速度。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js:41](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js#L41) |



##### wrapMode

> 动画的循环模式。

| meta | description |
|------|-------------|
| Type | <a href="../enums/WrapMode.html" class="crosslink">WrapMode</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js:51](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js#L51) |



##### curveData

> 曲线数据。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js:61](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js#L61) |

##### Examples

```js
{
    // 根节点不用查找路径
    // root properties
    props: {
        x: [
            { frame: 0, value: 0, curve: [0,0.5,0.5,1] },
            { frame: 1, value: 200, curve: null }
        ]
    },
    comps: {
        // component
        'comp-1': {
            // component properties
            'prop-1': [
                { frame: 0, value: 10, curve: [0,0.5,0.5,1] },
                { frame: 1, value: 20, curve: null }
            ]
        }
    },
    paths: {
        // key 为节点到root的路径名, 通过cc.find找到
        'foo/bar': {
            // node properties
            props: {
                x: [
                    { frame: 0, value: 0, curve: [0,0.5,0.5,1]
                    { frame: 1, value: 200, curve: null }
                ]
            },
            comps: {
                // component
                'comp-1': {
                    // component property
                    'prop-1': [
                        { frame: 0, value: 10, curve: [0,0.5,0.
                            { frame: 1, value: 20, curve: null }
                        ]
                        }
                }
            },
            'hello': {
                props: {
                    position: [
                        {
                            frame: 0,
                            value: [0,0],
                            motionPath: [
                                [320, 240, 0, 240, 640, 240],
                                [640, 0, 400, 0, 1000, 0]
                            ]
                        },
                        { frame: 5, value: [640, 480] }
                    ]
                }
            }
        }
    }
}
```


##### events

> 事件数据。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object[]</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js:73](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js#L73) |

##### Examples

```js
// frame    : The exactly time in second.
// func     : Callback function name
// params   : Callback parameters
[
    { frame: 0, func: 'onAnimationEvent1', params:['param-1', 'param-2'] },
    { frame: 2, func: 'onAnimationEvent3', params:['param-1', 'param-2'] },
    { frame: 3, func: 'onAnimationEvent2', params:['param-1'] },
    // The second event at frame 3
    { frame: 3, func: 'onAnimationEvent4', params:['param-1'] },
    { frame: 4, func: 'onAnimationEvent4', params:['param-1'] }
]
```


##### rawUrl

> 返回该资源的原始文件的 URL，如果不支持 RAW 文件，它将返回一个空字符串。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js:53](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js#L53) |



##### rawUrls

> 返回该资源的原文件的 URL 数组，如果不支持 RAW 文件，它将返回一个空数组。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String[]</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js:77](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js#L77) |



##### _rawFiles

> 在 lite 版的 Fireball 里，raw asset 并不仅仅是在 properties 里声明了 rawType 才有，
而是每个 asset 都能指定自己的 raw file url。这些 url 就存在 _rawFiles 字段中。
AssetLibrary 并不会帮你加载这些 url，除非你声明了 rawType。
在 Creator 里，_rawFiles 保留了下来，为了复用 cocos 引擎原有实现，直接用 _rawFiles 来加载 Asset 在 import 之前的源文件。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String[]</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js:104](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js#L104) |



##### _uuid

> 

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCRawAsset.js:48](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCRawAsset.js#L48) |



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

> 该对象的名称。

| meta | description |
|------|-------------|
| Type | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> |
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js:208](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/platform/CCObject.js#L208) |

##### Examples

```js
obj.name = "New Obj";
```


##### isValid

> 表示该对象是否可用（被销毁后将不可用）。

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


##### createWithSpriteFrames

使用一组序列帧图片来创建动画剪辑

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js:88](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/animation/animation-clip.js#L88) |
| Return 		 | <a href="../classes/AnimationClip.html" class="crosslink">AnimationClip</a> 

###### Parameters
- spriteFrames <a href="../classes/SpriteFrame.html" class="crosslink">[SpriteFrame]</a> 
- sample <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Number" class="crosslink external" target="_blank">Number</a> 

##### Example

```js
var clip = cc.AnimationClip.createWithSpriteFrames(spriteFrames, 10);
```

##### serialize

应 AssetDB 要求提供这个方法

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js:143](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js#L143) |
| Return 		 | <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> 



##### createNode

使用该资源在场景中创建一个新节点。<br/>
如果这类资源没有相应的节点类型，该方法应该是空的。

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js:154](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js#L154) |

###### Parameters
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 
	- error <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String</a> null or the error info
	- node <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object" class="crosslink external" target="_blank">Object</a> the created node or null


##### _setRawFiles

Set raw file names for this asset.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js:168](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js#L168) |

###### Parameters
- rawFiles <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/String" class="crosslink external" target="_blank">String[]</a> 


##### _preloadRawFiles

Preload raw files when loading scene.

| meta | description |
|------|-------------|
| Defined | [https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js:179](https:/github.com/cocos-creator/engine/blob/master/utils/api/engine/cocos2d/core/assets/CCAsset.js#L179) |

###### Parameters
- callback <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Function" class="crosslink external" target="_blank">Function</a> 
	- error <a href="https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Error" class="crosslink external" target="_blank">Error</a> 


##### destroy

销毁该对象，并释放所有它对其它对象的引用。<br/>
销毁后，CCObject 不再可用。您可以在访问对象之前使用 cc.isValid(obj) 来检查对象是否已被销毁。
实际销毁操作会延迟到当前帧渲染前执行。

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


