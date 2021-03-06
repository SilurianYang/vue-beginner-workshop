## Chapter 5

### Target

In this fifth chapter we will learn about Vue components. Components are a vital part of the Vue ecosystem.

Components allow for small, reusable pieces of code, independent of one and other to be composed together, building 
larger and more complex applications. This keeps each component small and easy to maintain, test and extend later on.

Components can communicate with each other by passing props down to child components and by emitting events to parent components.

### Challenges

#### What I will do:
1. Define a **House** component and move the `.house` element and required logic there
    - Register the **House** component on the main Vue instance as a local component.
    - Create a `text/x-template` script with an id of `house-template` in `index.html`, just below the `#app`.
        - Add the `#house-template` as a value for the House component's template property.
        - copy the `.house` element and its child elements to the newly defined template tag
    - Replace the old `.house` div with a `<house>` element where the old `.house` class used to be
      - Keep the v-for and key on the `<house>` component and not inside the `#house-template` script.
    - **Props** defined on the **House** component
      - **house** - _Object_ - The whole house object that contains the house name and the members
      - **currentHouse** - _String_ - The currently visible house
      - **houseId** - _String_ - The houseId of the current house.
    - Pass the **house**, **currentHouse** and **houseId** props to the `<house>` component.
    - Move the `isVisible` method from the main Vue instance to a computed property on **House**.
      - Remove the function parameter and use `this.houseId` instead. 
      - Update its usage on the `.members` div - it should not be a method call any more as its a property.
    - Bind a dynamic class to the `.house` element that sets a class equal to `houseId` and `is-active` based on `isVisible`. Use the array class binding syntax. `:class="[prop, { class1: prop1 }]"`
    - Check in Browser if **houses** are visible now.
    - Emit a `house-change` event when clicking the house
      - Add a `@click` handler on the `.house` element inside `#house-template` that emits `house-change` and pass the `houseId` as a payload - `$emit('house-change',houseId)`
    - Catch the `@house-change` event on the `<house>` component, in index.html, and call the `showHouse` method.

#### What you will do:
1. Define a **Members** component and move the `.members` element there
    - Define a **Members** component above the **House** component and register it as a local component on **House**.
    - Create a `text/x-template` script with an id of `members-template` and move the `.members` dropdown and its children from `#house-template` to it.
    - remove the `v-show/v-if` from `.members` div
    - Add a `template` property that equals to `#members-template`.
    - Add a `<members>` element in place of the `.members` class.
      - Keep the `isVisible` check on the `<members>` element.
    - **Props** defined on the **Members** component
      - **members** - Array - collection of members to display for each house
    - Pass **house.members** to the **members** prop
    - Change `house.members` to `members` in the v-for directive inside the template. This way it uses the prop, rather the members in the house, which are no longer available.
2. The main vue instance should just have the `#app`,`.map` and a loop of `<house/>` components.

#### Bonus:
1. Extract the **Member** component away from `.member` element.

