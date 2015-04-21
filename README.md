# mongo-map

When working with [mongoDB Aggregation Framework](http://docs.mongodb.org/manual/aggregation) sometimes you need to transform a filed based on plain js map object.
Consider you have:
```javascript
var map = {
	forThisKey: 'retrun this value',
	thisKeyEqualsTo: 'something like this',
	andForThisOne: 'return some other string'
};
```
In regular js code you would do:
```javascript
var value = map[key];
```
This module helps you do the same inside aggregation framework pipeline.

	npm install mongo-map

## Usage

```javascript
var getInMap = require('mongo-map');

db.myCollection.aggregate([
	{ $project: {
		value: getInMap(map, '$key')
	} }
]);
```
Here `getInMap` expands your map object into a balanced search tree that aggregation framework uses to look up your key.


## License

[MIT](http://opensource.org/licenses/MIT)
