# ember-computed-indirect

This is a small Ember addon that helps deal with indirect or dynamic computed properties. What this means
is that you can have one property store a reference to the property you would really like to watch,
getting updates when either the referenced property or the reference changes. Example:
 
```js
import computedIndirect from 'ember-computed-indirect/utils/indirect';

var object = Ember.Object.extend({
  source1: 'value1',
  source2: 'value2',
  path: 'source1',
  value: computedIndirect('path')
}).create();

object.get('value'); // 'value1'
object.set('value', 'newvalue');
object.get('source1'); // 'newvalue'
object.set('path', 'source2');
object.get('value'); // 'value2'
```

You can also access the function globally via `Ember.computed.indirect`. This may or may not be removed in the future,
but I'm going to keep it for now because I like the consistency with other Ember computed helpers.
