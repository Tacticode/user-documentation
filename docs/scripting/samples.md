# Scripting samples

These samples are useful functions you might want to use in your first scripts.

Make sure you understand what they do and how they work.

Feel free to improve or optimize them! They won't be enough for you to become the very best.

---

* Get the distance between two entities:

```js
function calcDistance(a, b) {
	return Math.abs(a.x - b.x) + Math.abs(a.y - b.y);
}
```

* Get the nearest alive enemy:

```js
function getNearestEnemy() {
	var me = getCurrentEntity();
	var entities = getEntities();
	var bestEnemy = null;
	var bestDistance = 9999;
	for (var i = 0; i < entities.length; ++i) {
		var e = entities[i];
		if (e.team != me.team && e.health > 0) {
			var distance = calcDistance(me, e);
			if (distance < bestDistance) {
				bestEnemy = e;
				bestDistance = distance;
			}
		}
	}
	return bestEnemy;
}
```

* Move towards an entity:

```js
function moveToEntity(e) {
	var me = getCurrentEntity();
	var movementPoints = me.movement;
	for (var i = 0; i < movementPoints; ++i) {
		if (me.x > e.x + 1) {
			moveToCell(me.x - 1, me.y);
		}
		if (me.x < e.x - 1) {
			moveToCell(me.x + 1, me.y);
		}
		if (me.y > e.y + 1) {
			moveToCell(me.x, me.y - 1);
		}
		if (me.y < e.y - 1) {
			moveToCell(me.x, me.y + 1);
		}
		me = getCurrentEntity();
	}
}
```