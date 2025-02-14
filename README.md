# Zustand - Lightweight yet Powerful State Manager for React

![Zustand bear](https://github.com/user-attachments/assets/e0ca20e6-aa9a-4c8b-9182-4ac37240829e)

[![npm версия](https://img.shields.io/npm/v/zustand.svg)](https://www.npmjs.com/package/zustand)

## Description

Zustand is a minimalist yet powerful state manager for React that provides a convenient API without unnecessary complexity.

## Installation

```sh
npm install zustand
# или
yarn add zustand
```

## Basic Usage

Let's create a simple store to manage a counter state:

```tsx
import create from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

export default useStore;
```

Using it in a component:

```tsx
import React from 'react';
import useStore from './store';

const Counter = () => {
  const { count, increment, decrement } = useStore();

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>+</button>
      <button onClick={decrement}>-</button>
    </div>
  );
};

export default Counter;
```

## Usage with TypeScript

Let's add type definitions for the store:

```tsx
import { create } from 'zustand';

interface CounterState {
  count: number;
  increment: () => void;
  decrement: () => void;
}

const useStore = create<CounterState>((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

export default useStore;
```

Now TypeScript will automatically ensure type safety when working with the store.

## Middleware

Zustand supports middleware for logging, persistence, and other functionalities.

### 1. Logging State Changes

```tsx
import { create } from 'zustand';
import { devtools } from 'zustand/middleware';

const useStore = create(
  devtools((set) => ({
    count: 0,
    increment: () => set((state) => ({ count: state.count + 1 })),
    decrement: () => set((state) => ({ count: state.count - 1 })),
  }))
);
```

### 2. Persisting State

```tsx
import { create } from 'zustand';
import { persist } from 'zustand/middleware';

const useStore = create(
  persist(
    (set) => ({ count: 0, increment: () => set((state) => ({ count: state.count + 1 })) }),
    { name: 'counter-storage' }
  )
);
```

### 3. Combining Middleware

You can combine multiple middleware:

```tsx
import { create } from 'zustand';
import { persist, devtools } from 'zustand/middleware';

const useStore = create(
  devtools(
    persist(
      (set) => ({ count: 0, increment: () => set((state) => ({ count: state.count + 1 })) }),
      { name: 'counter-storage' }
    )
  )
);
```

## Usage with React Context

Zustand does not require context, but if you want to pass the store through context:

```tsx
import { createContext, useContext } from 'react';
import create from 'zustand';

const StoreContext = createContext(null);

export const StoreProvider = ({ children }) => {
  const store = useStore();
  return <StoreContext.Provider value={store}>{children}</StoreContext.Provider>;
};

export const useSharedStore = () => useContext(StoreContext);
```

## Subscribing to State Changes

```tsx
import useStore from './store';

useStore.subscribe((state) => {
  console.log('Состояние обновлено:', state);
});
```

## Async Operations (API Requests)

```tsx
import { create } from 'zustand';

interface TodoState {
  todos: string[];
  fetchTodos: () => Promise<void>;
}

const useTodoStore = create<TodoState>((set) => ({
  todos: [],
  fetchTodos: async () => {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos?_limit=5');
    const data = await response.json();
    set({ todos: data.map((todo: any) => todo.title) });
  },
}));
```

Using it in a component:

```tsx
const TodoList = () => {
  const { todos, fetchTodos } = useTodoStore();
  return (
    <div>
      <button onClick={fetchTodos}>Загрузить задачи</button>
      <ul>{todos.map((todo, index) => <li key={index}>{todo}</li>)}</ul>
    </div>
  );
};
```

## Additional Features

- `setState(partialState)`: updates part of the state
- `getState()`: retrieves the current state
- `destroy()`: unsubscribes listeners
- `subscribe(listener)`: subscribes to state changes
