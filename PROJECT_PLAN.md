# COZY ART — Многостраничный сайт с CMS

## 📋 Обзор проекта

Многостранический сайт для компании "COZY ART — Архитектурный бетон" с headless CMS и полной SEO-оптимизацией.

## 🏗 Технологический стек

### Frontend
- **Next.js 14+** (App Router) — React фреймворк с серверным рендерингом
- **TypeScript** — типобезопасность
- **Tailwind CSS** — утилитарные стили
- **GSAP + ScrollTrigger** — анимации
- **next-seo** — SEO оптимизация
- **next-sitemap** — генерация sitemap

### Backend & CMS
- **Sanity.io** — headless CMS (или Strapi при необходимости self-hosted)
- **Groq** — быстрый запрос данных из Sanity

### Инфраструктура
- **Docker & Docker Compose** — контейнеризация
- **Nginx** — reverse proxy
- **Node.js 20** — runtime

## 📁 Структура проекта

```
cozy-art-site/
├── apps/
│   ├── web/                          # Next.js приложение
│   │   ├── app/
│   │   │   ├── (site)/               # Основные страницы сайта
│   │   │   │   ├── layout.tsx        # Layout с header/footer
│   │   │   │   ├── page.tsx          # Главная страница
│   │   │   │   ├── catalog/
│   │   │   │   │   ├── page.tsx      # Каталог товаров
│   │   │   │   │   └── [slug]/
│   │   │   │   │       └── page.tsx  # Страница категории
│   │   │   │   ├── products/
│   │   │   │   │   └── [slug]/
│   │   │   │   │       └── page.tsx  # Страница товара
│   │   │   │   ├── process/
│   │   │   │   │   └── page.tsx      # Процесс производства
│   │   │   │   ├── projects/
│   │   │   │   │   ├── page.tsx      # Портфолио проектов
│   │   │   │   │   └── [slug]/
│   │   │   │   │       └── page.tsx  # Страница проекта
│   │   │   │   ├── about/
│   │   │   │   │   └── page.tsx      # О компании
│   │   │   │   ├── blog/
│   │   │   │   │   ├── page.tsx      # Блог (список)
│   │   │   │   │   └── [slug]/
│   │   │   │   │       └── page.tsx  # Статья блога
│   │   │   │   └── contacts/
│   │   │   │       └── page.tsx      # Контакты
│   │   │   ├── api/
│   │   │   │   ├── revalidate/       # On-demand ISR
│   │   │   │   └── contact/          # Обработка форм
│   │   │   ├── robots.ts             # Robots.txt
│   │   │   ├── sitemap.ts            # Sitemap.xml
│   │   │   └── layout.tsx            # Root layout
│   │   ├── components/
│   │   │   ├── ui/                   # Базовые UI компоненты
│   │   │   │   ├── Button.tsx
│   │   │   │   ├── Card.tsx
│   │   │   │   ├── Section.tsx
│   │   │   │   └── ...
│   │   │   ├── layout/               # Компоненты layout
│   │   │   │   ├── Header.tsx
│   │   │   │   ├── Footer.tsx
│   │   │   │   └── MobileMenu.tsx
│   │   │   ├── sections/             # Секции страниц
│   │   │   │   ├── HeroSection.tsx
│   │   │   │   ├── CategoriesSection.tsx
│   │   │   │   ├── ProductsSection.tsx
│   │   │   │   ├── ProcessSection.tsx
│   │   │   │   ├── ProjectsSection.tsx
│   │   │   │   ├── StatsSection.tsx
│   │   │   │   ├── ContactSection.tsx
│   │   │   │   └── ...
│   │   │   ├── product/              # Компоненты товаров
│   │   │   │   ├── ProductCard.tsx
│   │   │   │   ├── ProductGrid.tsx
│   │   │   │   └── ProductFilters.tsx
│   │   │   ├── project/              # Компоненты проектов
│   │   │   │   ├── ProjectCard.tsx
│   │   │   │   └── ProjectGallery.tsx
│   │   │   ├── blog/                 # Компоненты блога
│   │   │   │   ├── PostCard.tsx
│   │   │   │   └── PostContent.tsx
│   │   │   └── seo/                  # SEO компоненты
│   │   │       ├── PageSEO.tsx
│   │   │       └── StructuredData.tsx
│   │   ├── lib/
│   │   │   ├── sanity/               # Sanity клиент и запросы
│   │   │   │   ├── client.ts
│   │   │   │   ├── queries.ts
│   │   │   │   └── types.ts
│   │   │   ├── utils.ts              # Утилиты
│   │   │   ├── animations.ts         # GSAP конфигурации
│   │   │   └── constants.ts          # Константы
│   │   ├── hooks/                    # Custom React hooks
│   │   │   ├── useScrollAnimation.ts
│   │   │   └── useMediaQuery.ts
│   │   ├── styles/
│   │   │   ├── globals.css           # Глобальные стили
│   │   │   └── tailwind.css          # Tailwind директивы
│   │   ├── public/
│   │   │   ├── images/
│   │   │   ├── fonts/
│   │   │   └── favicon.ico
│   │   ├── types/                    # TypeScript типы
│   │   │   └── index.ts
│   │   ├── next.config.js
│   │   ├── tailwind.config.ts
│   │   ├── tsconfig.json
│   │   └── package.json
│   │
│   └── cms/                          # Sanity CMS (опционально self-hosted)
│       ├── schemas/                  # Схема контента
│       │   ├── page.ts
│       │   ├── product.ts
│       │   ├── category.ts
│       │   ├── project.ts
│       │   ├── post.ts
│       │   ├── author.ts
│       │   ├── siteSettings.ts
│       │   └── seo.ts
│       ├── deskStructure.ts
│       ├── package.json
│       └── sanity.config.ts
│
├── docker/
│   ├── web/
│   │   └── Dockerfile
│   ├── nginx/
│   │   ├── Dockerfile
│   │   └── nginx.conf
│   └── scripts/
│       └── init.sh
│
├── docs/
│   ├── DEPLOYMENT.md                 # Инструкция по развертыванию
│   ├── CMS_GUIDE.md                  # Руководство по CMS
│   └── SEO_CHECKLIST.md              # SEO чеклист
│
├── .env.example                      # Пример переменных окружения
├── .gitignore
├── docker-compose.yml                # Docker Compose конфигурация
├── package.json                      # Root package.json
└── README.md                         # Этот файл
```

## 📊 Модель данных CMS (Sanity)

### Основные типы контента:

1. **Page** — Страницы сайта
   - title, slug, seo, body (Portable Text), sections[]

2. **Product** — Товары
   - name, slug, description, price, category, images[], specs[], seo

3. **Category** — Категории товаров
   - name, slug, description, image, parent (для вложенности)

4. **Project** — Проекты (портфолио)
   - title, slug, description, client, location, year, images[], challenges[], solutions[], seo

5. **Post** — Статьи блога
   - title, slug, excerpt, body, author, publishedAt, coverImage, tags[], seo

6. **Author** — Авторы блога
   - name, bio, image, social[]

7. **SiteSettings** — Глобальные настройки
   - siteName, logo, contactInfo, socialLinks, defaultSeo

8. **SEO** — Переиспользуемый SEO объект
   - metaTitle, metaDescription, ogImage, canonicalUrl

## 🚀 Пошаговый план реализации

### Этап 1: Инициализация проекта (День 1)
- [ ] 1.1 Создать структуру монорепозитория
- [ ] 1.2 Настроить Next.js 14 с TypeScript
- [ ] 1.3 Настроить Tailwind CSS с кастомной темой (цвета из шаблона)
- [ ] 1.4 Настроить ESLint, Prettier, Husky
- [ ] 1.5 Создать базовую конфигурацию Docker

### Этап 2: Настройка CMS (День 2)
- [ ] 2.1 Зарегистрировать проект на Sanity.io (или настроить локально)
- [ ] 2.2 Создать схемы контента (product, category, project, post, page)
- [ ] 2.3 Настроить Sanity Studio
- [ ] 2.4 Создать начальный контент (демо-данные)
- [ ] 2.5 Настроить GROQ запросы

### Этап 3: Базовые компоненты (День 3-4)
- [ ] 3.1 Создать UI компоненты (Button, Card, Section, Container)
- [ ] 3.2 Реализовать Header с адаптивным меню
- [ ] 3.3 Реализовать Footer
- [ ] 3.4 Настроить систему анимаций (GSAP + ScrollTrigger)
- [ ] 3.5 Создать хуки для анимаций

### Этап 4: Главная страница (День 5)
- [ ] 4.1 Перенести дизайн из HTML-шаблона в React компоненты
- [ ] 4.2 Hero секция с Canvas анимацией
- [ ] 4.3 Секция категорий
- [ ] 4.4 Секция популярных товаров
- [ ] 4.5 Секция процесса
- [ ] 4.6 Секция статистики
- [ ] 4.7 Секция контактов
- [ ] 4.8 Интеграция с CMS для динамического контента

### Этап 5: Каталог и товары (День 6-7)
- [ ] 5.1 Страница каталога с фильтрами
- [ ] 5.2 Страница категории товаров
- [ ] 5.3 Страница отдельного товара
- [ ] 5.4 Компонент галереи изображений
- [ ] 5.5 Компонент характеристик товара

### Этап 6: Проекты и портфолио (День 8)
- [ ] 6.1 Страница списка проектов
- [ ] 6.2 Страница отдельного проекта
- [ ] 6.3 Галерея проекта с лайтбоксом
- [ ] 6.4 Секция "до/после" (если нужно)

### Этап 7: Дополнительные страницы (День 9)
- [ ] 7.1 Страница "О компании"
- [ ] 7.2 Страница "Процесс производства" (расширенная)
- [ ] 7.3 Страница контактов с формой
- [ ] 7.4 Обработчик формы обратной связи

### Этап 8: Блог (День 10)
- [ ] 8.1 Страница списка статей
- [ ] 8.2 Страница статьи
- [ ] 8.3 Система тегов и категорий
- [ ] 8.4 Блок "похожие статьи"

### Этап 9: SEO оптимизация (День 11)
- [ ] 9.1 Настроить next-seo для всех страниц
- [ ] 9.2 Реализовать мета-теги из CMS
- [ ] 9.3 Настроить Open Graph изображения
- [ ] 9.4 Создать sitemap.xml
- [ ] 9.5 Создать robots.txt
- [ ] 9.6 Добавить структурированные данные (Schema.org)
- [ ] 9.7 Настроить canonical URLs

### Этап 10: Производительность (День 12)
- [ ] 10.1 Оптимизация изображений (next/image)
- [ ] 10.2 Настройка ISR (Incremental Static Regeneration)
- [ ] 10.3 Lazy loading компонентов
- [ ] 10.4 Оптимизация шрифтов
- [ ] 10.5 Audit Lighthouse и исправления

### Этап 11: Docker и деплой (День 13)
- [ ] 11.1 Создать Dockerfile для Next.js
- [ ] 11.2 Настроить Nginx конфигурацию
- [ ] 11.3 Создать docker-compose.yml
- [ ] 11.4 Настроить переменные окружения
- [ ] 11.5 Протестировать локальный запуск
- [ ] 11.6 Документация по деплою

### Этап 12: Тестирование и финализация (День 14)
- [ ] 12.1 Кроссбраузерное тестирование
- [ ] 12.2 Тестирование на мобильных устройствах
- [ ] 12.3 Проверка всех форм
- [ ] 12.4 Проверка SEO (meta tags, sitemap)
- [ ] 12.5 Финальные правки дизайна
- [ ] 12.6 Документация для клиента

## 🔧 Docker конфигурация

###docker-compose.yml будет включать:
- **web** — Next.js приложение (production build)
- **nginx** — Reverse proxy, SSL termination
- **sanity** — (опционально) локальная Sanity Studio

### Переменные окружения (.env):
```bash
# Sanity CMS
NEXT_PUBLIC_SANITY_PROJECT_ID=xxx
NEXT_PUBLIC_SANITY_DATASET=production
SANITY_API_TOKEN=xxx

# Site
NEXT_PUBLIC_SITE_URL=https://cozyart.ru
NODE_ENV=production

# Contact Form
EMAIL_SERVICE_HOST=smtp.example.com
EMAIL_SERVICE_PORT=587
EMAIL_USER=noreply@cozyart.ru
EMAIL_PASSWORD=xxx
```

## 📈 SEO возможности

- ✅ Динамические meta title/description из CMS
- ✅ Open Graph изображения для соцсетей
- ✅ Twitter Cards
- ✅ Canonical URLs
- ✅ Sitemap.xml (автогенерация)
- ✅ Robots.txt
- ✅ Structured data (JSON-LD)
- ✅ ЧПУ URL
- ✅ Микроразметка Schema.org (Organization, Product, Article)
- ✅ Hreflang (если нужна мультиязычность)

## 🎨 Дизайн система

Сохраняем стиль из шаблона:
- **Цвета**: Темная тема (#141414, #1E1E1E) с акцентом #B8956A
- **Шрифты**: Inter (основной), Space Grotesk (заголовки)
- **Анимации**: Плавные GSAP переходы, параллакс эффекты
- **Компоненты**: Карточки с hover эффектами, стеклянный морфизм

## 📝 Следующие шаги

После утверждения плана:
1. Инициализируем репозиторий с правильной структурой
2. Настроим окружение и зависимости
3. Подключим Sanity CMS
4. Начнем реализацию с главной страницы

---

**Готов приступить к реализации. Подтвердите план или внесите корректировки.**
