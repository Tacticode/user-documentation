# Getting started

Scripting is the main core mechanism of Tacticode. In order to win your fights and climb in the ladder, you need a powerful algorithm.

-----

## Javascript introduction

Scripts are written in Javascript. The goal of this game is not to teach you the ropes of programming, we expect you to be able to write code already. Do not worry though, you do not need to take any advanced programming course to play Tacticode.

What you **must** know before playing:

- Imperative programming
- Functions, variables and control structures
- How to read an API

What you **should** know before playing:

- A pathfinding algorithm (to move your character)
- A line drawing algorithm (to check the line of sight)

## Useful resources

* [Learn X in Y minutes, where X=Javascript](https://learnxinyminutes.com/docs/javascript/)
* [Wikipedia: Dijkstra's algorithm](https://en.wikipedia.org/wiki/Dijkstra's_algorithm)
* [Wikipedia: Line drawing algorithm](https://en.wikipedia.org/wiki/Line_drawing_algorithm)
* [Mozilla: JavaScript reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)

-----

## Main function

All scripts must implement the `onTurn` function. This function will be called at the beginning of the player turn.

```js
function onTurn() {
	// The player behaviour goes there.
}
```

For instance, if you want to cast the spell _Holy Hand_ on your character, you can call the `cast` function.

```js
function onTurn() {
	cast("HOLY_HAND");
}
```

Provided that your character possesses the specified spell, it will be casted on your character every turn.

If you want to execute two actions, like moving then casting a spell, you can write the two commands naturally:

```js
function onTurn() {
	moveToCell(8, 2);
	cast("FIREBALL", 8, 3);
}
```

Your character will try to move to the cell _[8, 2]_ then cast the spell _Fireball_ on the cell _[8, 3]_.

## Retrieving information

Being able to move and cast spells is not enough if you do not know where to move or where to cast the spells.

You can retrieve information about the current fight using the getter functions, like `getEntities()` or `getCell(x, y)`.

For instance, if you want your character to move to the cell next to them, you could use the following code:

```js
function onTurn() {
	var me = getCurrentEntity();
	moveToCell(me.x + 1, me.y);
}
```

Or, you can decide to cast a fireball on the first entity in the list. (be careful, it might be you or an ally!)

```js
function onTurn() {
	var entities = getEntities();
	var firstEntity = entities[0];
	cast("FIREBALL", firstEntity.x, firstEntity.y);
}
```

There you go! You now have all the information required to start writing your first scripts.

You might want to check the [Scripting samples](samples.md) to gather useful functions.
