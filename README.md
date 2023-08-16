# "ClassKAFC" - Оптимізація Організації Навчання в Навчальному закладі

В рамках проекту ClassKAFC, я взяв на себе завдання оптимізувати організацію навчання в моєму колледжі, використовуючи сучасні технології. Цей проект націлено на вдосконалення способу, яким викладачі надсилають та студенти отримують навчальні завдання.

## Проблема
Раніше кожен викладач надсилав завдання по-різному:

- Один надсилав їх старості через електронну пошту.
- Інший розсилав їх усім студентам одразу.
- Третій використовував різні канали для різних груп.

Це призводило до великої кількості неврегульованих завдань, втрати документів та збиткового розподілу матеріалів.

## Рішення
"ClassKAFC" був створений для вирішення цієї проблеми. Я розробив веб-додаток, який забезпечує викладачів зручним і єдиним способом надсилання завдань студентам. Тепер викладачі можуть звертатися до централізованої платформи, вказуючи деталі завдань та додаючи необхідні файли. Більше не потрібно слідкувати за тим, хто отримав завдання, а хто ні

## Особливості
У моєму веб-додатку для викладачів реалізовано зручний інтерфейс, де вони можуть легко вказувати деталі завдань та додавати необхідні матеріали перед надсиланням студентам. Завдяки інтегрованому боту у Telegram, студенти отримують повідомлення про нові завдання та можуть зручно переглядати їх та зберігати відповідні матеріали.

## Використані Технології
У цьому проекті я використовував наступні технології:

- Flask для створення веб-додатку
- pyTelegramBotAPI для взаємодії з Telegram-ботом
- Celery для оптимізації відправки завдань студентам
- Amazon S3 для безпечного зберігання завантажених файлів
- Postgres з SQLAlchemy для взаємодії з базою даних
Всі ці компоненти обгорнуті в docker-compose для зручності розробки та розгортування.

## Висновок
Проект "ClassKAFC" представляє мої навички у вирішенні реальних проблем за допомогою сучасних технологій.
Розробка веб-додатку та Telegram-бота в цьому проекті відображає мою спроможність створювати практичні рішення для покращення організаційних процесів.

# Quick Start

Для швидкого запуску та налаштування додатку, виконайте наступні кроки:

#### Крок 1: Налаштування ngrok
Завантажте та встановіть ngrok.
Створіть файл ngrok.yml у корені проекту з наступним вмістом:

```yaml
authtoken: ваш_ключ_автентифікації
version: 2
tunnels:
  students-bot:
    proto: http
    addr: host.docker.internal:5000
```
#### Крок 2: Налаштування .env файлу
Створіть файл .env у корені проекту з наступними змінними середовища:
```
SECRET_KEY=ваш_секретний_ключ
DATABASE_URL=postgresql+psycopg2://root:123@postgres:5432/class
BOT_TOKEN=ваш_токен_бота
REDIS_URL=redis://redis:6379
AWS_ACCESS_KEY=ваш_ключ_доступу_AWS
AWS_SECRET_KEY=ваш_секретний_ключ_AWS
BUCKET_NAME=назва_вашого_bucket
```
Замість відповідних значень підставте власні дані.

#### Крок 3: Запуск
Виконайте команду docker-compose up для запуску додатку.
```bash
docker-compose up
```
Після запуску контейнера classkafc, встановіть вебхук для бота за допомогою команди:
```bash
docker exec -it classkafc flask set-webhook
```
