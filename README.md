![Zustand bear](https://github.com/user-attachments/assets/e0ca20e6-aa9a-4c8b-9182-4ac37240829e)

# Zustand — Управление состоянием в React

[![npm версия](https://img.shields.io/npm/v/zustand.svg)](https://www.npmjs.com/package/zustand)
[![Лицензия: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

Этот проект демонстрирует использование **Zustand** — легковесной и гибкой библиотеки для управления состоянием в приложениях на React. Zustand упрощает управление как локальным, так и глобальным состоянием с минимальным количеством шаблонного кода и предоставляет отличные оптимизации производительности через реактивное хранилище.

## Оглавление

- [Обзор](#обзор)
- [Ключевые особенности](#ключевые-особенности)
- [Установка](#установка)
- [Начало работы](#начало-работы)
- [Пример базового использования](#пример-базового-использования)
- [Продвинутое использование](#продвинутое-использование)
- [Производительность](#производительность)
- [Сообщество и поддержка](#сообщество-и-поддержка)
- [Лицензия](#лицензия)

## Обзор

Zustand — это маленькая, быстрая и масштабируемая библиотека, которая позволяет управлять состоянием приложения с простотой и гибкостью. Это особенно полезно, когда требуется легковесная альтернатива более крупным решениям для управления состоянием, таким как Redux или Context API. Zustand предлагает упрощенный API без ущерба для мощности и масштабируемости.

## Ключевые особенности

- **Минимум шаблонного кода**: Требует значительно меньше кода по сравнению с Redux или MobX.
- **Селективные обновления состояния**: Компоненты перерисовываются только при изменении той части состояния, от которой они зависят.
- **API на основе React Hooks**: Легко интегрируется с React-хуками.
- **Поддержка персистентности**: Встроенная поддержка сохранения состояния в `localStorage` или `sessionStorage`.
- **Поддержка TypeScript**: Полная поддержка TypeScript для обеспечения типобезопасности.

## Установка
Вы можете установить Zustand с помощью npm или yarn:

```bash
npm install zustand
```
```bash
yarn add zustand
```

## Начало работ
Создайте хранилище: Определите состояние и действия с помощью функции create.
Используйте хранилище: Подписывайтесь на состояние в компонентах с помощью хуков React.
Обновляйте состояние: Вызывайте действия для изменения состояния, что приведет к перерисовке только тех компонентов, которые зависят от обновленного состояния.

## Пример базового использования
Пример использования Zustand в проекте React:

```js
import create from 'zustand';

// Создаем хранилище
const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  reset: () => set({ count: 0 }),
}));

// Используем хранилище в компоненте
function Counter() {
  const count = useStore((state) => state.count);
  const increment = useStore((state) => state.increment);
  const reset = useStore((state) => state.reset);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>Увеличить</button>
      <button onClick={reset}>Сбросить</button>
    </div>
  );
}
```

## Продвинутое использование
Zustand также поддерживает продвинутые сценарии использования, такие как:
Персистентное состояние: Сохранение состояния в localStorage или sessionStorage.
Множественные хранилища: Разделение состояния на несколько независимых хранилищ.
Мидлвары и плагины: Добавление функционала через мидлвары, такие как журналирование или откат состояния.

## Производительность
Zustand оптимизирует работу с состоянием за счет подписок на конкретные части состояния, что значительно уменьшает количество перерисовок компонентов. Компоненты React обновляются только тогда, когда меняется та часть состояния, от которой они зависят.

## Сообщество и поддержка
- Официальный репозиторий на GitHub: [Zustand](https://github.com/pmndrs/zustand)
- Вопросы и обсуждения: [Обсуждения](https://github.com/pmndrs/zustand/discussions)
- Сообщество в Discord: [Reactiflux](https://reactiflux.com/)

## Лицензия
Этот проект распространяется под лицензией MIT. Подробнее см. LICENSE.

```markdown

Этот `README.md` предоставляет пользователю всю необходимую информацию о библиотеке **Zustand**, а также ключевые моменты, чтобы легко начать работу и интегрировать её в проект.
```

