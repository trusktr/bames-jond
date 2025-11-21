# <img src="./logo/Favicon_BamesJond.svg" height="32" /> Bames Jond

The name's Jond, Bames Jond.

## Summary

Hire Bames Jond to take action on your targets.

Use `bames-jond` to react to changes of properties in objects.

![](./logo/Logo-Full_BamesJond-Color.svg)

## Usage

### `observe(obj)`/`unobserve(obj)`

Observe particular properties of an object (non-deeply).

```js
import * as bames from 'bames-jond'

const janous = {
	name: 'Alex Travelin',
	stats: {
		kills: 6,
	},
	kill(someone) {
		console.log('killed ' + someone)
		this.stats.kills++
	},
}

const callback = (key, value) => {
	console.log(key, value)
}

bames.observe(janous, ['name'], callback)
bames.observe(janous.stats, ['kills'], callback)

setTimeout(() => {
	janous.name = 'Janous' // logs "name Janous"
	janous.kill('soldier') // logs "kills 7"
}, 1000)
```

Later, unobserve when mission accomplished:

```js
// Unobserve all props for the given callback (in this case, just "kills")
bames.unobserve(janous.stats, callback)
// Alternatively, unobserve specific props for the given callback.
bames.unobserve(janous, ['name'], callback)
```

## Next stop?

Jond is always on the move.

- Add deferral options, f.e. to have updates batched into a microtask or
  animation frame.
