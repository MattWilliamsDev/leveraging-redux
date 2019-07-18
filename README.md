**Leveraging the Power of React (and Redux!)**

1. Introduction

    1. Personal Info

        1. Name & Employer

        2. Experience

    2. Thesis

        3. React's architecture style and community make it arguably the best front-end framework on the market that allows us to reduce code duplication, lowers the worries associated with keeping data synchronized across multiple models that we see in MV* frameworks, and allows devs to create reusable libraries of individual, configurable components to facilitate speedy development and/or prototyping.

        4. Combining React with Redux allows devs to build high quality, highly scalable applications without many of the headaches that typically come with trying to scale React-based applications. (like shared state)

2. Why React?

    3. Simplicity

        5. Easy to Learn

        6. JSX

        7. View layer only

        8. All boils down to vanilla JS

        9. Performance - Virtual DOM allows for rapid view updates

    4. Component-based Architecture

        10. Allows for the creation of reusable libraries of components that can greatly speed up the development process.

        11. Incredibly reusable, scaleable, and composable allow components to be used in a wide variety of situations and use-cases.

        12. Allows us to utilize the Single Responsibility Principle (SRP)

        13. Create apps with "building blocks" that can easily be configured or tailored to specific use cases

        14. HUGE online community making it easy to find 3rd party tools, get support for issues, and make it easier to hire and onboard devs

    5. HUGE Community

        15. Well-established and scalable patterns that are widely available makes finding/hiring/assimilating developers with specific skills far easier.

        16. Numerous 3rd party libs that simplify most complex or tedious tasks, often in a more robust fashion than possible while developing other applications

        17. Incredible support community - most questions you encounter WILL already have an answer.

        18. Makes hiring and on-boarding easier to have such widely known, used, and accepted methods/frameworks for development

            1. Don’t need to learn as many implementation-specific details or "foibles" to become productive in an environment

    6. Incredible Testability

        19. Having numerous tiny components that are responsible for a single thing each lends itself incredibly well to testing as scope is able to stay small for each component

        20. More granular tests === more reliable tests

        21. ReactJS applications are super easy to test. React views can be treated as functions of the state, so we can easily manipulate them for testing with state we pass to the component.

    7. Other Advantages

        22. React DevTools

3. Why Redux?

    8. What is Redux?

        23. Dispatch Actions to a Reducer function that then mutates state predictably based on provided data

            2. Actions look like this:

                1. { type: "MY_ACTION_NAME", payload: someData }

                2. { type: "MY_ACTION_NAME" }

            3. Reducer

                3. Describes how the state will be mutated

                4. Pure functions - side-effect free

                5. Return new objects (allows easy ref comparison)

                6. glorified switch statement with action.type being the key

                7. Looks like this:

                    1. { [myAction]: (state, payload) => ({ ...state, myProperty: payload.updatedValue }) }

            4. Dispatch

                8. Used to "trigger" actions and send them to the application reducer

            5. Store

                9. This is the application state represented as a series of objects

                10. This is the "single source of truth" in the app

    9. No more multi-level "prop drilling" needed

    10. Keeps state synchronized throughout the application

        24. Provides a "single source of truth" in your app

        25. All components have a single reference to a given piece of data so if you update the state from one place, it is displayed properly everywhere else that utilizes that piece of state

        26. Ex: Component A gets customerName and uses it as the default value in a form. Component B displays "Hello, [customerName]". Both stay in sync automatically as the state is mutated

        27. Focus on immutability allows for speedy comparison in the change detection cycle, speeding up the most expensive part of frontend apps - (re)rendering

    11. Does everyone need Redux?

        28. No. Not all apps need this much scalability or state management

    12. Signs you DO need Redux

        29. Multiple components need to access a shared piece of state but don’t share a parent

        30. In general, use Redux when you have reasonable amounts of data changing over time, you need a single source of truth, and you find that approaches like keeping everything in a top-level React component's state are no longer sufficient.

        31. "Prop Drilling" has become tedious and there are multiple components that have props passed through them that don’t need said props just so they can be passed to a child component.

    13. Advantages of Redux

        32. Encourages good React architecture

        33. Implements performance optimizations for you by maintaining immutability

        34. Large community surrounding Redux both with and without React

        35. Simplified React components

            6. We were able to flatten our React component structure and even remove some container components. This was because we no longer needed to organise the hierarchy of components around passing data downwards.

            7. We were able to convert some class components to functional components.

        36. Separation of concerns

            8. Having a distinct section of our application that described all of the actions and reducer functions made it easier for new developers to get a quick overview of the business logic of our app in a single place.

            9. Our React components became less bloated with state and functions that updated state. This meant our components could just focus on managing the User Interface and were much more readable.

        37. Quality

            10. Easily debuggable state

            11. Redux is ridiculously easy to write unit tests for.

                11. Mock store

    14. Tooling Advantages

        38. Redux DevTools - See a list of actions and jump to them to examine your app in a given state and understand how data is mutated throughout your app

        39. Redux Logger/LogRocket - A production Redux logging tool that lets you replay problems as if they happened in your own browser. Instead of guessing why errors happen, or asking users for screenshots and log dumps, LogRocket lets you replay Redux actions + state, network requests, console logs, and see a video of what the user saw.

        40. Numerous other tools

4. React and Redux Together

    15. Integration

        41. Configuring Store

            12. Middleware (Thunk, History)

            13. ConnectedRouter

            14. Root Reducer

    16. connect() vs useDispatch and useMappedState

        42. Class vs Functional Components

        43. Sync vs Async Actions

        44. Examples

5. Summary

    17. Redux isn’t THAT intense/tough

    18. Not everyone **needs** Redux

    19. Redux Developer Tools are INCREDIBLE

6. Links

    20. Libraries

        45. Redux

            15. Redux Starter Kit: [https://github.com/reduxjs/redux-starter-kit](https://github.com/reduxjs/redux-starter-kit)

            16. Redux Thunk: [https://github.com/reduxjs/redux-thunk](https://github.com/reduxjs/redux-thunk)

            17. Redux Mock Store: [https://github.com/dmitry-zaets/redux-mock-store](https://github.com/dmitry-zaets/redux-mock-store)

            18. ConnectedRouter: [https://github.com/supasate/connected-react-router](https://github.com/supasate/connected-react-router)

            19. Redux Logger/LogRocket: [https://github.com/LogRocket/redux-logger](https://github.com/LogRocket/redux-logger)

            20. Redux DevTools (Chrome): [https://github.com/zalmoxisus/redux-devtools-extension](https://github.com/zalmoxisus/redux-devtools-extension)

[https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd)

            21. Redux React Hooks: [https://github.com/facebookincubator/redux-react-hook](https://github.com/facebookincubator/redux-react-hook)

        46. React

            22. Classnames: [https://github.com/JedWatson/classnames](https://github.com/JedWatson/classnames)

            23. Formik: [https://github.com/jaredpalmer/formik](https://github.com/jaredpalmer/formik)

        47. Other

            24. **TypeScript: **[https://www.typescriptlang.org/](https://www.typescriptlang.org/)
