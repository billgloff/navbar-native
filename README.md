# NavbarNative
A **fully customizable** Navbar component for React-Native.
#### It works for both iOS and Android!

![navbar-native-intro](https://cloud.githubusercontent.com/assets/1061849/18530527/3bdab2b6-7ad2-11e6-95e4-1774e625080d.png)

![navbar-native-intro-android](https://cloud.githubusercontent.com/assets/1061849/18553248/0970cbd8-7b60-11e6-8b72-ec91f4d98671.png)

### Content
- [Installation](#installation)
- [Exported components](#exported-components)
- [Getting started](#getting-started)
- [Images as title](#image-as-title)
- [Container API](#container-api)
- [Navbar API](#navbar-api)
- [Demo](#demo)

### Installation
```bash
npm i navbar-native --save
```

### Pay attention
This package depends on the beautiful [Vector Icons for React Native](https://github.com/oblador/react-native-vector-icons).

After installing NavbarNative, in order to have **icons working**, please follow instructions about [HOW TO INSTALL AND LINK VECTOR ICONS](https://github.com/oblador/react-native-vector-icons) in your project.

### Exported components
This package exports two main components:

- **Container** - a container component to use as the first component in a __render()__ method. It accepts the "Navbar" component and the rest of the page content.
- **Navbar** - the components which generates the bar on top.

### Getting started
Basically, the Navbar component accepts a **title** prop and **left** and/or **right** objects (or array of objects) which describe each button that the navbar has to render in the specific position.

#### Using icons
In order to use the correct set of icons, please use **ios-** prefix in _icon_ prop name for iOS and **md-** prefix for Android.

The following chunk of code shows a typical **iOS** NavbarNative usage:

```js
import React, { Component } from 'react';
import { View } from 'react-native';

import { Container, Navbar } from 'navbar-native';

class ReactNativeProject extends Component {
    render() {
        return (
            <Container>
                <Navbar
                    title={"Navbar Native"}
                    left={{
                        icon: "ios-arrow-back",
                        label: "Back",
                        onPress: () => {alert('Go back!')}
                    }}
                    right={[{
                        icon: "ios-search",
                        onPress: () => {alert('Search!')}
                    },{
                        icon: "ios-menu",
                        onPress: () => {alert('Toggle menu!')}
                    }]}
                />
                ... other stuff ...
            </Container>
        );
    }
}
```

### Image as a title

![image_list](https://cloud.githubusercontent.com/assets/1061849/18619404/6b15bb58-7dfb-11e6-917d-9c3ca6547f4f.png)

You can also use a **remote** or **local** image instead of the text title:

```js
class ReactNativeEmpty extends Component {
    render() {
        return (
            <Container type="list" data={["first", "second", "third"]}>
                <Navbar
                    user={true}
                    image={{
                        source:'https://facebook.github.io/react/img/logo_og.png',
                        type: 'remote',
                        resizeMode: 'cover'
                    }}
                    statusBar={{
                        style: "default",
                        hideAnimation: Navbar.FADE,
                        showAnimation: Navbar.SLIDE,
                    }}
                    left={{
                        icon: "ios-arrow-back",
                        label: "Back",
                        onPress: () => {alert('Go back!')}
                    }}
                    right={[{
                        icon: "ios-search",
                        onPress: () => {alert('Search!')}
                    },{
                        icon: "ios-menu",
                        onPress: () => {alert('Toggle menu!')}
                    }]}
                />
            </Container>
        );
    }
}
```

### Image as background

![image-background](https://cloud.githubusercontent.com/assets/1061849/18619959/0e4003b2-7e09-11e6-9ec5-d88a43b0ed2c.png)

Images can be used in **background** also:

```js
class ReactNativeEmpty extends Component {
    render() {
        return (
            <Container type="list" data={["first", "second", "third"]}>
                <Navbar
                    user={true}
                    title={"Navbar Native"}
                    titleColor="white"
                    imageBackground={{
                        source:'https://facebook.github.io/react/img/logo_og.png',
                        type: 'remote',
                        resizeMode: 'cover'
                    }}
                    statusBar={{
                        style: "light-content",
                        hideAnimation: Navbar.FADE,
                        showAnimation: Navbar.SLIDE,
                    }}
                    left={{
                        icon: "ios-arrow-back",
                        iconColor: "white",
                        label: "Back",
                        onPress: () => {alert('Go back!')},
                        style:{color: 'white'}
                    }}
                    right={[{
                        icon: "ios-search",
                        iconColor: "white",
                        onPress: () => {alert('Search!')}
                    },{
                        icon: "ios-menu",
                        iconColor: "white",
                        onPress: () => {alert('Toggle menu!')}
                    }]}
                />
            </Container>
        );
    }
}
```

### Container API
- **data** - (Array of strings or Array of Objects) - data source for ListView
- **row** - (React component opt.) - Component that renders single roe element in ListView
- **style** - (Object) - Custom styles for the container,
- **type** - ('scroll' or 'list' def. 'scroll') - How to render Container children content

### Navbar API
- **title** - (String opt.) - The title string
- **titleColor** - (String opt.) - The title string color
- **tintColor** - (String def. '#ffffff') - NavigationBar's background tint color
- **image** - (Object opt.) - Local/remote image instead of the title
  - **source** - (String) - Local/remote image location
  - **type** - ('local' or 'remote' def. 'local') - Origin of the image
  - **resizeMode** - ('cover', 'contain', 'stretch', 'repeat', 'center' def. 'cover')
  - **style** - (Object opt.) - Additional styles for image title
- **imageBackground** - (Object opt.) - Local/remote image in navbar background
  - **source** - (String) - Local/remote image location
  - **type** - ('local' or 'remote' def. 'local') - Origin of the image
  - **resizeMode** - ('cover', 'contain', 'stretch', 'repeat', 'center' def. 'cover')
  - **style** - (Object opt.) - Additional styles for image background  
- **statusBar** - (Object opt.):
  - **style** - ('light-content' or 'default') - Style of statusBar
  - **hidden** - (Boolean)
  - **tintColor** - (String) - Status bar tint color
  - **hideAnimation** - ('fade', 'slide', 'none') - Type of statusBar hide animation
  - **showAnimation** - ('fade', 'slide', 'none') - Type of statusBar show animation
- **left / right** - (Object or Array of Objects):
  - **icon** - (String opt.) - Vector Icon's icon name
  - **iconFamily** - (String def. Ionicons) - Vector Icon's icon library
  - **iconPos** - ('left' or 'right' def. left/right position) - Icon's position towards the label
  - **iconSize** - (Number def. 30 ios - 28 android) - Icon's size
  - **iconColor** - (String def. '#0076FF' ios - '#FFFFFF' android) - Icon's color
  - **label** - (String opt.) - Button's label
  - **onPress** - (Function) - onPress function handler
  - **role** - (String opt. - 'back' | 'close' | 'login' | 'menu') - Button's pre-defined aspect
  - **style** - (Object opt.) - Button's override styles
- **style** - (Object) - Custom styles for the navbar
- **user** - (Object, Bool) - Authenticated user

### Demo

Check an advanced implementation [HERE](https://github.com/redbaron76/MeteorNative)

![react-native-intro](https://cloud.githubusercontent.com/assets/1061849/18615649/5f3c930a-7dac-11e6-9d52-eef4b56b8d21.gif)
