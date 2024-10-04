# Restaurant Menu App

This project is a simple restaurant menu application built with React. The app allows users to filter items based on their category (e.g., breakfast, lunch, shakes). It's a great beginner-level project for practicing React fundamentals, such as using state, props, components, and basic filtering functionality.

## Table of Contents

- Features
- Technologies Used
- Project Setup
- Step-by-Step Guide
  - Step 1: Create React Components
  - Step 2: Data Management with useState
  - Step 3: Filtering Menu Items
  - Step 4: Rendering Components
  - Step 5: Optimize the Code
- Explanation of Using Set()
- Run the Project
- Thank You!

## Features

- Display a menu of items with image, title, price, and description.
- Filter menu items based on their category (e.g., breakfast, lunch, shakes).
- Dynamic rendering of categories based on the available items.
- Responsive layout (if styled with responsiveness in mind).

## Technologies Used

- React (functional components, hooks like useState)
- JavaScript ES6+ features like Set() and arrow functions
- HTML5 for the structure
- CSS3 for styling

## Project Setup

- Clone the repository or download the source code.
  ````git clone https://github.com/your-repo/restaurant-menu-app.git
  cd restaurant-menu-app```
  ````
- Install the necessary dependencies using npm or yarn:

```bash

npm install

# or

yarn install
```

- Start the development server:

```bash
npm start

# or

yarn start
```

### Step 1: Create React Components

The app is broken down into smaller, reusable components for better maintainability. Here’s the basic structure of components:

- App.js: The main component that manages state and passes props to child components.
- Categories.js: Displays category buttons that allow users to filter items by category.
- Menu.js: Renders a list of filtered menu items.
- MenuItem.js: Displays individual menu items.

**This modular approach makes it easy to manage and expand the app.**

### Step 2: Data Management with useState

React's useState hook is used to manage two states in this app:

- menuItems: Holds the list of items to be displayed (filtered or not).
- categories: Holds the list of categories for filtering.

```js
const [menuItems, setMenuItems] = useState(items);
const [categories, setCategories] = useState(allCategories);
```

- Step 3: Filtering Menu Items
  The app provides buttons to filter the menu items by category. This is achieved using the **filterItems** function, which checks the category of each menu item and updates the menuItems state.

```js
const filterItems = (category) => {
  if (category === "all") {
    setMenuItems(items);
    return;
  }
  const newItems = items.filter((item) => item.category === category);
  setMenuItems(newItems);
};
```

When the "all" category is selected, the entire menu is displayed. Otherwise, the function filters the items based on their category.

### Step 4: Rendering Components

Each menu item is rendered as a separate component using map(). The Menu component is responsible for rendering the list of items by passing down the filtered menuItems as props to MenuItem.

```js
<Menu items={menuItems} />
```

Each individual item is displayed by the MenuItem component, which receives props like the image, title, price, and description.

### Step 5: Optimize the Code

To avoid recalculating the list of categories on every render, the allCategories array is created outside the App component. This ensures it’s computed only once:

```js
const allCategories = ["all", ...new Set(items.map((item) => item.category))];
```

This line uses Set() to get unique categories from the items array, then spreads those values into an array and adds "all" as the first category. This ensures that category buttons are dynamically created based on the available menu items.

**important**

## Why use Set()

We use Set() here to ensure that each category is unique when we dynamically create the filtering buttons. A Set in JavaScript only stores unique values, so when we map through the items array to extract the categories, the Set removes any duplicates. This ensures that we don't create multiple buttons for the same category.

Here’s how it works:

```js
const allCategories = ["all", ...new Set(items.map((item) => item.category))];
```

- items.map((item) => item.category): This extracts all categories from the items array.
- new Set(...): The Set constructor takes an iterable (like an array) and removes any duplicate values, leaving only unique categories.
- [...new Set(...)]: The spread operator (...) converts the Set back into an array.
- ["all", ...]: We add "all" at the beginning to allow users to reset the filter and view all items.
  This approach ensures that our category buttons are created dynamically based on the data and that there are no duplicate categories.

> **Thank you for your interest! Contributions and feedback are always welcome**
