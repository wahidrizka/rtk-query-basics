## 🌟 Introduction

This project is a simple React application that demonstrates the usage of Redux Toolkit Query (RTK Query) to fetch and display Pokémon data from the [PokeAPI](https://pokeapi.co/). 🐾 The application includes components for listing Pokémon and displaying details of a selected Pokémon. It is structured with a main `App` component, a `PokemonList` component, and a `PokemonDetails` component. The code utilizes TypeScript for type definitions and includes a Redux store configuration for managing API state.

## ⚙️ Setup

### 📋 Prerequisites

- ✅ Node.js and npm installed on your machine.
- ✅ Basic knowledge of React and Redux.

### 📥 Installation

1. **Clone the Repository:**

  ```bash
  git clone https://github.com/your-username/my-pokedex.git
  cd my-pokedex
  ```

2. **Install Dependencies:**

  ```bash
  npm install
  ```

3. **Run the Application:**

  ```bash
  npm start
  ```

  🚀 This will start the development server and open the application in your default web browser.

## 🛠️ Usage

### 🔍 Overview

The application consists of two main components:

- **PokemonList:** 📝 Displays a list of Pokémon. Clicking on a Pokémon's name will navigate to the details page.
- **PokemonDetails:** 📊 Shows detailed information about the selected Pokémon, including its ID, height, weight, and types.

### 🧩 Components

#### 🏠 App Component

- **Functionality:** The main component that manages the state of the selected Pokémon and renders either the `PokemonList` or `PokemonDetails` component based on the state.

#### 📜 PokemonList Component

- **Functionality:** Fetches a list of Pokémon from the PokeAPI and displays them in an ordered list.
- **Props:**
  - `onPokemonSelected`: A callback function that updates the selected Pokémon's name in the `App` component.

#### 🔍 PokemonDetails Component

- **Functionality:** Fetches detailed information about a selected Pokémon from the PokeAPI and displays it.
- **Props:**
  - `pokemonName`: The name of the Pokémon to fetch details for.

### 🛠️ Redux Toolkit Query (RTK Query)

RTK Query is used to manage API state and data fetching in this application. It simplifies the process of fetching data and updating the UI in response to API responses.

#### 📡 API Definition:

```typescript
const api = createApi({
  baseQuery: fetchBaseQuery({
   baseUrl: "https://pokeapi.co/api/v2/",
  }),
  endpoints: (build) => ({
   pokemonList: build.query<PokemonListing, void>({
    query() {
      return {
       url: "pokemon",
       params: { limit: 9 },
       method: "GET",
      };
    },
   }),
   pokemonDetail: build.query<PokemonDetailData, { name: string }>({
    query: ({ name }) => `pokemon/${name}/`,
   }),
  }),
});
```

#### 🔗 Hooks:

- `usePokemonListQuery`: Fetches the list of Pokémon.
- `usePokemonDetailQuery`: Fetches detailed information about a selected Pokémon.

### 🎯 Project Goals

This project is intended to serve as an introduction and application walkthrough for the basics of Redux Toolkit Query. It demonstrates how to set up and use RTK Query in a React application to manage API state and data fetching efficiently.

### 🏁 Conclusion

This simple application provides a clear and concise example of how to use Redux Toolkit Query in a React project. It covers the essential aspects of setting up RTK Query, defining API endpoints, and using hooks to fetch and display data. Feel free to explore and modify the code to deepen your understanding of RTK Query and its capabilities. 🎉