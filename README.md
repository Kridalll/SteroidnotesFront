# Web-приложение для ведения умных заметок "Steroid Notes"

## Установка зависимостей

Сначала установите зависимости NPM.

```bash
npm i
```

### Настройка стека Supabase

Чтобы собрать проект нам потребуется база данных которая будет нашим основным хранилищем - это Supabase, причём мы можем как разрабатывать локально, так и непосредственно в облаке.

#### Локально

1. Запустите локальную версию Supabase _(работает в Docker)_.

    ```shell
    npx supabase start
    ```

2. Сохраните URL и публичный анонимный ключ Supabase в `.env.local` для Next.js.

    ```bash
    npx supabase status -o env \
      --override-name api.url=NEXT_PUBLIC_SUPABASE_URL \
      --override-name auth.anon_key=NEXT_PUBLIC_SUPABASE_ANON_KEY |
        grep NEXT_PUBLIC > .env.local
    ```

#### В облаке

1. Создайте проект Supabase на [https://database.new](https://database.new) или через CLI:

    ```shell
    npx supabase projects create -i "ChatGPT Your Files"
    ```

    ID вашей организации можно найти в URL после [выбора организации](https://supabase.com/dashboard/org/_/general).

2. Свяжите ваш CLI с проектом.

    ```shell
    npx supabase link --project-ref=<project-id>
    ```

    Можно получить ID проекта со страницы [общих настроек](https://supabase.com/dashboard/project/_/settings/general).

3. Сохраните URL и публичный анонимный ключ Supabase в `.env.local` для Next.js.

    ```shell
    NEXT_PUBLIC_SUPABASE_URL=<api-url>
    NEXT_PUBLIC_SUPABASE_ANON_KEY=<anon-key>
    ```

    Можно получить API URL проекта и анонимный ключ из [страницы настроек API](https://supabase.com/dashboard/project/_/settings/api).

## Использованные технологии

- [`Next.JS`](https://nextjs.org/)
- [`Supabase + pg_vector`](https://supabase.com/docs/guides/database/extensions/pgvector)
- [`Lexical`](https://lexical.dev/docs/intro)
