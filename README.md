 1 import map from 'map.js';
 2 import basePickBy from './.internal/basePickBy.js';
 3 import getAllKeysIn from './.internal/getAllKeysIn.js';
 4 
 5 /**
 6  * Creates an object composed of the `object` properties `predicate` returns
 7  * truthy for. The predicate is invoked with two arguments: (value, key).
 8  */
 9 function pickBy(object, predicate) {
10   if (object == null) {
11     return {};
12   }
13   const props = map(getAllKeysIn(object), prop => [prop]);
14   return basePickBy(object, props, (value, path) => predicate(value, path[0]));
15 }
16 
17 export default pickBy;
