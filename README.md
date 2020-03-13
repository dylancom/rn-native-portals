[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

_This repository hasn't been published yet, I need some help to expose the native component to JS. The current status should be working on android like described in https://github.com/mfrachet/rn-native-portals/issues/1#issuecomment-419985453_

[Here's the story _why_ we've built this library](https://t.co/QVGbfGuLG3)

React Native implementation of [ReactDOM portals](https://reactjs.org/docs/portals.html) using a declarative API.

This library makes possible the _teleportation_ of views from a place to another one.

---

# Content

- <a href="#usage">How to use it ?</a>
- [Understanding the concept](./docs/CONCEPT.md)

<h1 name="#usage">Usage</h1>

### Installation

```
$ yarn add mfrachet/rn-native-portals

# Using iOS
$ cd ios && pod install
```

### In your code

Somewhere high in your component tree, add a `PortalDestination` (a portal destination):

```javascript
import {  PortalDestination } from "rn-native-portals";

render() {
	return (
		<PortalDestination name="targetOfTeleportation" />
	);
}
```

Somewhere else in the tree, add a `PortalOrigin` (a portal origin):

```javascript
import { PortalOrigin } from 'rn-native-portals';

render() {
	return (
		<PortalOrigin destination={ this.state.shouldMove ? 'targetOfTeleportation' : null }>
			<View>
				<Text>Hello world</Text>
			</View>
		</PortalOrigin>
	);
}
```

When the `shouldMove` state will change to something truthy, the `View` and the `Text` components will be moved inside the `PortalDestination` component set
previously.

If the value of the `destination` prop is set to `null`, the `View` and `Text` are restituted to their original place.

---

Built with ❤️ at [M6 Web](http://tech.m6web.fr/)
