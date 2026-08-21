# Bike Theft Tracker

React SPA for a bike-rental company to log and track bike-theft cases — with
JWT authentication, role-based access, and a REST API backend.

*Educational final project (2023). Kept public as part of my learning trajectory —
this was the first project where I worked against a real API with authentication
rather than static data.*

## Problem

A bike-rental company operating across several Russian cities was losing bikes to
theft and had no structured way to record incidents or track what happened to
them afterwards. Their backend team had built the API; the client application
needed to be built against it.

## Solution

A single-page application with two distinct access levels:

- **Public users** get a limited surface — the landing page and a form to report a
  new theft case. No account needed.
- **Company staff** sign in and get the full case-management view: browsing and
  updating cases, viewing officer records, and internal messaging.

## Key features

- **JWT authentication** — sign-up and sign-in flows; the token is persisted to
  `localStorage` and attached as an `Authorization: Bearer` header on subsequent
  requests.
- **Role-based rendering** — the interface branches on whether the signed-in user
  is staff, so public visitors never see the management views.
- **Case management** — create, browse and update theft cases against the REST API.
- **Officer directory** — list and detail views for staff records.
- **Responsive layout** built on React-Bootstrap, with a burger menu on mobile.

## Architecture

```
App.js                       auth state, session handling, routing
components/
  Home/                      public landing page
  Report/                    public theft-report form
  Signin/  Signup/           authentication flows
  AllOfficers/               officer list + detail views
  Messages/                  internal staff messaging
  Header/  Footer/           shared layout
```

Auth state and session are lifted to `App.js` and passed down; the token in
`localStorage` is what survives a page reload.

## Tech stack

React 18 · React Router 6 · axios · React-Bootstrap · REST API (external backend)

## How it works

```bash
npm install
npm start      # http://localhost:3000
npm run build
```

The API base is `sf-final-project-be.herokuapp.com` — the backend was provided as
part of the assignment and may no longer be reachable, so a fresh checkout may not
be able to sign in today.

## My role

Built the entire client application — routing, authentication flow, API
integration, role logic and layout. The backend was provided.

## Challenges / lessons

First project where I had to handle a real authentication lifecycle rather than
mock data: storing a token, attaching it to requests, deciding what the UI shows
before and after sign-in, and handling the case where a request comes back
unauthorized. Conditional rendering by role also forced me to think about
component structure up front instead of improvising it.

## Status

Archived — educational project, completed 2023. Not in active development.

---

## Русская версия

**Что это:** SPA на React для компании по прокату велосипедов — учёт и
отслеживание случаев кражи, с JWT-авторизацией, ролевым доступом и REST API.

*Учебный финальный проект (2023). Оставлен публичным как часть траектории
обучения — это был первый проект, где я работал с реальным API и авторизацией,
а не со статичными данными.*

**Задача:** компания, сдающая велосипеды в аренду в крупных городах России,
теряла имущество из-за краж и не имела структурированного способа фиксировать
случаи и отслеживать их прогресс. Серверную часть подготовила их команда —
нужно было реализовать клиентскую.

**Решение:** одностраничное приложение с двумя уровнями доступа. Обычному
пользователю доступна ограниченная часть — главная страница и форма, чтобы
сообщить о новой краже, без регистрации. Сотрудники компании авторизуются и
получают полный доступ: работа с делами, справочник сотрудников, внутренние
сообщения.

**Ключевое:**

- **JWT-авторизация** — регистрация и вход, токен сохраняется в `localStorage`
  и подставляется в заголовок `Authorization: Bearer` последующих запросов.
- **Ролевой рендеринг** — интерфейс ветвится в зависимости от того, вошёл ли
  сотрудник, так что публичные посетители не видят управляющие разделы.
- **Управление делами** — создание, просмотр и обновление случаев кражи через REST API.
- **Справочник сотрудников** — списки и детальные карточки.
- **Адаптивная вёрстка** на React-Bootstrap с бургер-меню на мобильных.

**Стек:** React 18 · React Router 6 · axios · React-Bootstrap · внешний REST API.

**Запуск:** `npm install` → `npm start` (http://localhost:3000). База API —
`sf-final-project-be.herokuapp.com`, бэкенд выдавался в рамках задания и может
быть уже недоступен, поэтому на свежей копии вход может не работать.

**Моя роль:** полностью клиентское приложение — роутинг, авторизация, интеграция
с API, ролевая логика и вёрстка. Бэкенд был предоставлен.

**Что было сложным:** первый проект, где пришлось работать с настоящим жизненным
циклом авторизации, а не с моковыми данными: хранение токена, подстановка его в
запросы, решение о том, что интерфейс показывает до и после входа, и обработка
ответа, когда запрос возвращается неавторизованным. Условный рендеринг по ролям
также заставил продумывать структуру компонентов заранее, а не по ходу.

**Статус:** архив — учебный проект, завершён в 2023, не развивается.
