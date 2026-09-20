# MERIDIAN — Портфолио (Vue.js)

## Запуск

```bash
npm install
npm run dev
```

Сборка:

```bash
npm run build
```

## Компоненты

- `FilterInput.vue` — поле поиска с `v-model` (`modelValue` + `$emit('update:modelValue')`)
- `ProjectList.vue` — список карточек через `v-for` и `v-if`
- `ProjectCard.vue` — карточка проекта, данные через `props`
