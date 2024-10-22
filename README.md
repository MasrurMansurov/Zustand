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
- [Вклад в проект](#вклад-в-проект)
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

