# Руководство для разработчиков

## Описание

Это репозиторий с полезными советами и рекомендациями. Здесь собраны ответы на часто возникающие вопросы и инструкции.

## Содержание

- [Руководство для разработчиков](#руководство-для-разработчиков)
  - [Описание](#описание)
  - [Содержание](#содержание)
    - [Создание токена для клонирования приватного репозитория](#создание-токена-для-клонирования-приватного-репозитория)
    - [Совместная работа над проектом](#совместная-работа-над-проектом)
    - [Правила написания заголовков коммитов](#правила-написания-заголовков-коммитов)
    - [Единый стиль кода с использованием Prettier ESLint](#единый-стиль-кода-с-использованием-prettier-eslint)
      - [Эффективная работа с VS Code для повышения продуктивности](#эффективная-работа-с-vs-code-для-повышения-продуктивности)
    - [Именование переменных](#именование-переменных)

---

### Создание токена для клонирования приватного репозитория

Чтобы клонировать приватный репозиторий, вам потребуется создать персональный токен доступа. Это можно сделать через настройки вашего аккаунта на GitHub:

1. Перейдите в `Settings > Developer settings > Personal access tokens`.
2. Нажмите "Generate new token", выберите необходимые права для доступа (`repo`).
3. Скопируйте сгенерированный токен (он отображается только один раз).

Пример команды для клонирования с использованием токена:

```bash
git clone https://<ваш-токен>@github.com/ваш-логин/private-repo.git
```

В этом примере:

- `<ваш-токен>` — это ваш сгенерированный токен.
- `ваш-логин` — это ваш логин на GitHub.
- `private-repo` — это название приватного репозитория, который вы клонируете.

---

### Совместная работа над проектом

Когда вы работаете над новым функционалом, придерживайтесь следующего алгоритма:

1. **Создание новой ветки:** Всегда создавайте отдельную ветку для каждой задачи или фичи.

   Пример:

   ```bash
   git checkout -b feature/add-authentication
   ```

   Эта команда создаёт ветку под названием `feature/add-authentication` и автоматически переключает вас на неё.

   Элементы:

   - `git checkout -b`: эта команда создаёт новую ветку и переключает вас на неё.
   - `feature/add-authentication`: это имя новой ветки. Оно состоит из двух частей:
     - `feature`: префикс, который указывает на тип работы (в данном случае, добавление новой функциональности).
     - `add-authentication`: описание конкретной задачи или фичи, над которой ведётся работа.

2. **Добавление изменений в коммит:** Перед тем как сделать коммит, добавьте изменённые файлы в индекс с помощью команды `git add`.

   Пример:

   ```bash
   git add .
   ```

   Это добавит все изменённые файлы в коммит. Вы также можете добавить конкретные файлы, указав их имя:

   ```bash
   git add path/to/file.js
   ```

3. **Коммит изменений:** Выполняйте коммиты в вашу ветку с понятными заголовками. Если изменений много, делайте несколько коммитов.

   Пример:

   ```bash
    git commit -m "feat: Added authentication functionality"
   ```

4. **Создание Pull Request:**

   1. Перейдите на страницу репозитория на GitHub.
   2. Нажмите на вкладку **Pull Requests** и выберите **New Pull Request**.
   3. Выберите вашу ветку в поле **compare** и убедитесь, что основная ветка (обычно `main` или `master`) выбрана в поле **base**.
   4. Добавьте заголовок и описание Pull Request, поясняя изменения, которые были внесены.
   5. Нажмите **Create Pull Request**.

После создания Pull Request, необходимо упомянуть (тегнуть) ответственного за проверку кода в комментариях, чтобы уведомить его о необходимости проведения code review. Пример:

```
@username, could you please review this PR?
```

---

### Правила написания заголовков коммитов

Чтобы облегчить навигацию по истории изменений проекта, используйте стандарт [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/). Это поможет улучшить навигацию по коммитам и упростить их ревью.

Примеры форматов:

- **fix:** исправление ошибки.  
  Пример: `fix: resolved issue with data loading`
- **feat:** добавление новой функциональности.  
  Пример: `feat: implemented user authentication feature`

Следование этим правилам поможет быстрее ориентироваться в истории коммитов и понимать суть изменений.

---

### Единый стиль кода с использованием Prettier ESLint

Смотрять не могу на кодстайл из серии _"Строки на экране выдаются строго по талонам"_

Для того чтобы наш код был единообразным и легко читаемым, необходимо использовать линтеры. Мы используем Prettier и ESLint, которые помогают поддерживать единый стиль написания кода и предотвращать типичные ошибки.

**Что такое линтер?**
Линтер — это инструмент, который анализирует код на наличие ошибок и отклонений от принятого стиля. Prettier отвечает за форматирование, а ESLint проверяет соответствие кода стилевым соглашениям и стандартам.

**Шаги для настройки:**

1. Установите необходимые плагины Prettier и ESLint для вашего редактора (например, в VS Code).
2. Настройте форматирование кода:
    - ПКМ по файлу > **Configure Default Formatter** > **Prettier ESLint**.
    - Включите автоформатирование при сохранении: `editor.formatOnSave: true`.

Для форматирования вручную: **Shift + Alt + F**.

---

#### Эффективная работа с VS Code для повышения продуктивности

Для повышения удобства работы в VS Code ознакомьтесь с [10 рекомендациями по работе в VS Code](https://habr.com/ru/companies/ruvds/articles/765182/). Обратите внимание на:

- Пункт №2 - Autosave: хватит использовать Ctrl + S.
- Пункт №8 - Быстрое форматирование кода.

---

### Именование переменных

Корректное именование переменных — это основа читаемого кода. Следуйте следующим рекомендациям:

1. Используйте понятные и самодокументирующиеся имена переменных.
2. Придерживайтесь стиля `camelCase` для переменных и функций.
3. Не используйте аббревиатуры и слишком короткие имена, если это не оправдано.

Пример:

```javascript
let userAge = 25; // Понятно, что переменная содержит возраст пользователя
let totalAmount = 1000; // Переменная обозначает общую сумму
```

Полная документация - [Практическим руководством по именованию классов, функций и переменных](https://habr.com/ru/articles/558874/).
