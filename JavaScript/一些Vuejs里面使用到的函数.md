
```js
/**
 * 类型判断
 * Get the raw type string of a value e.g. [object Object]
 */
var _toString = Object.prototype.toString;
function toRawType (value) {
  console.log(value)
  console.log(_toString)
  return _toString.call(value).slice(8, -1)
}
toRawType()             // "Undefined"
toRawType(undefined)    // "Undefined"
toRawType(null)         // "Null"
toRawType("1")          // "String"
toRawType(1)            // "Number"
toRawType([])           // "Array"
toRawType({})           // "Object"

```