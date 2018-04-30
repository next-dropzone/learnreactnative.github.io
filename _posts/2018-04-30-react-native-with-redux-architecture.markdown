---
layout: post
title: React Native with Redux Architecture
date: 2018-04-29 00:00:00 +0300
description: React Native is a popular user interface (UI) library for mobile app development.
img: react-native-with-redux-architecture.png
tags: [react native, mobile, mobile app, mobile development, react, react native training, learn react native]
---

In an application of any scale or complexity, the user interface (which is also often called the view layer) only constitutes a part of the overall application functionality. Another very important part is the data or modal layer, which is responsible for fetching data from web servers, persisting the data, and managing data updates to and from the view layer.

React Native is a popular user interface (UI) library for mobile app development. Because it has no guidelines or defined patterns for managing data within an application, it can be used with practically any framework or library. That being said, developers have increasingly been searching for a data management solution created specifically with React in mind and that shares some of its principles.

One solution that developers have turned to is Facebook's Flux architecture. Flux is not an implementation; it is an architecture much like the Model-View-Controller architecture that is implemented by frameworks like Backbone or Angular. Flux provides a design pattern that must be implemented by an application or library developer. The central theme of the Flux architecture is unidirectional data flow and the reduction of a shared mutable state. Redux is the implementation of the Flux architecture, which has become the most popular in the React Native developer community.

### Mobile Application with Redux Architecture

The architecture diagram shown below; how Redux fits together with React Native in a mobile application. It shows the key components of the application, the relations among them, and the properties of both. As mentioned earlier, the responsibility of an application's view layer is handled by React Native components, where the data or model layer of the application is handled by Redux. Native modules are another small but important part of the application. These modules of the code are written in Native platforms (iOS/Android) for functionalities that are not available in React Native.

![react native organize structure](/assets/img/react-native-redux-diagram.png)

Below is a brief description of each of components from this architecture.

### View Layer

The view layer consists of the user interface and business logic of the application. In the view layer, an application's screen transitions are handled with the help of navigator and container components.

#### Container Components

Containers are smart components that manage the flow of data to other components, called presentational components. Containers are responsible for connecting with the store to pass the information to their child components and provide actions and callbacks for children. From an application's navigation view-point, containers should be the only components that are referenced in navigator routes. Also, container components should not contain any rendering of view, except for the composition of presentational components.

#### Presentational Components

Presentational components are pure user interface components and are only concerned with rendering the views. These components will internally use React Native UI components (e.g., TouchableOpacity, Button, ListView, Text, TextInput, Image, Animations, etc.) and other third-party components to achieve the desired user interface. Presentational components are responsible for encapsulating the view creation, style, gestures, and animations into isolated components, which can then be reused at multiple places in the application. Thus, an application's view layer will have a collection of such reusable presentation components to accelerate the development of the application.

Presentational components are contained within the container components and will interact with them with the help of callbacks. As per the design principles of React, each presentational component has its own state and styles, and it is customized based on the properties it receives from its parent container component. Some styling properties (e.g., fonts, colors, date format, etc.) are common across all the presentational components. These common styling properties are part of the common styles javascript files, and hence are shared by all the presentational components.

The view layer will have a collection of such reusable presentational components, which will accelerate the development of application features and screens.

#### Navigators

The key container components handle the screen transitions within the application. The required combination of drawer navigator, stack navigator, etc. must be used to achieve the desired application navigation.

#### Common

Some application codes, colors, fonts, etc. will be common and shared across all the components. These common items are categories, and they fall into the below categories:

* Utilities: The utility folder contains individual utility JS files. These files are based on a group of utility functions like DateUtility, NetworkRequestUtility, etc. These files contain individual functions exports for each function under the respective utility group. Below are some of the utility files which are common to most of mobile applications. More utility files should be identified during the detail design of an application.

* Common Style Properties (Colors, Fonts, etc.): Here, the rule of thumb is to reuse components, not styles. Each component will have its own set of styles, but the values of these style can be common for colors, fonts, border radius, etc. These common values are kept in the CommonStyleValues.js file, which has export statements for each of the values.

### Redux Layer

As mentioned above, the Redux layer is the data or model layer of the application. It includes:

#### Actions

An action is a JavaScript object that has both a type and, optionally, a payload of data. An action object is created by the component, ideally by the container components, as a result of user interaction. The type of the action is a constant string that reflects the interaction’s intent. Action type is enough for the reducers to deduce the effect on the application state.

#### Reducers

In Redux, a reducer is a pure function that takes the previous state and an action as input and then returns the new state. Since in Redux all application states are contained within a single store that is a single large JavaScript object, it’s the individual reducers that are responsible for managing the smaller parts of this large application state object. Developers will typically modularize the reducers, organizing them into separate files and naming each reducer to correspond to the key for the part of the state object it is managing.

#### Store

All application states are contained within a single store – a single large JavaScript object. The store is one large data structure of key value pairs. Using these keys, view components subscribe to the changes to the Redux store application state in which they are interested. Whenever there is an update in the application state, the render cycle of the respective components is triggered.

Since all application states are kept in the dynamic storage (heap/ram) of the mobile device, if a user comes back to a screen that has already been rendered, the respective screen will be quickly loaded with the data it was holding. This level of dynamic data caching is achieved inherently with Redux store.

#### Redux-thunk (Middleware)

Redux is optimized for synchronous workflow. Actions are dispatched synchronously, and the view layer is updated accordingly. But in real applications, some things cannot be done synchronously; operations like fetching data from a server are done asynchronously. To accommodate asynchronous operations, Redux provides a middleware. Middleware is injected between the dispatching of an action and its arrival at the reducer. Redux-thunk is one of the most popular middleware options to handle asynchronous operations in Redux.

Redux-thunk is responsible for managing asynchronous operations. Since it's a Redux middleware, this thread can be started, paused, and canceled from the main application with normal Redux actions. It has access to the full Redux application state store, and it can dispatch Redux actions as well.

#### Native Code Layer

Native modules in the layer consist of the code written in Native platforms (iOS/Android) for functionalities that are not possible in React Native. This will be a very thin layer that should not be more than 10-20% of the application code. If it’s more than that, then you may need to reconsider your application development platform choice.

### Key Architectural Goals

Below are the key architectural goals met by this architecture.

#### Reusability

Reusability defines the capability for components and subsystems to be suitable for use in other applications and in other scenarios. Reusability minimizes the duplication of components and implementation time.

To achieve maximum reusability of the code across iOS and Android platforms, this architecture is built on a React Native framework. With React Native, not only the code but also the engineering skill set is reused. Since it’s based on a “learn once, work anywhere” approach, the same set of engineers are able to build applications for both platforms without needing to learn the fundamentally different set of technologies for each platforms. This results  in quicker development cycles and reduced time-to-market.

Another aspect of this architecture that helps reusability is the separation of container and presentational components. This will lead to the creation of a set of reusable presentational components that can be reused in multiple places in the application — and also in other applications.

#### Extensibility

Extensibility is the ability of a system to allow and accept a significant extension of its capabilities, without majorly rewriting its code or making changes to its basic architecture.

To achieve extensibility in the system, we have integrated the Redux framework to handle the model layer of the application. This provides a complete separation of the model and presentation layers, thus allowing each to grow independently and help maintain the overall complexity of the application.

To achieve extensibility in the system, we have integrated the Redux framework to handle the model layer of the application. This provides a complete separation of the model and presentation layers, thus allowing each to grow independently and help maintain the overall complexity of the application.

So far the Redux architecture is suitable for a wide range of mobile applications. It's a well-tested and proven design, and it provides a baseline infrastructure to build. For iOS and Android mobile application developers who are accustomed to thinking from a MVC and MVP design perspective, this architecture provides a fresh outlook and eases the transition from Native development to cross-platform development.
