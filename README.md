# README: Olej Klonowski – Full-Stack E-commerce Platform

## 🌿 Wprowadzenie

"Olej Klonowski" to nie tylko platforma e-commerce – to cyfrowe sanktuarium, w którym technologia spotyka się z duchowością, a użytkownik odnajduje spokój, zdrowie i naturę. Platforma oferuje ręcznie tłoczone oleje, naturalne mikstury i treści edukacyjne, wspierając klientów w ich podróży ku harmonii ciała i ducha.

Ten dokument README przedstawia kluczowe informacje o strukturze projektu, technologiach oraz zasadach implementacyjnych całego systemu.

---

## 📐 Architektura Systemu

Platforma jest zbudowana w modelu headless z oddzielnymi komponentami:

- **Frontend (Next.js + Tailwind CSS)** – SEO-friendly, SSR, z pełną responsywnością, dostępnością (a11y) i przygotowaną internacjonalizacją (i18n).
- **Backend (NestJS + PostgreSQL + TypeORM)** – modularna architektura (produkty, zamówienia, użytkownicy, AI, treści), REST API (ew. GraphQL), JWT-auth, ORM.
- **Baza Danych** – PostgreSQL, relacyjne połączenia między produktami, użytkownikami, zamówieniami, partiami i treściami.
- **AI Agent System (Flowise)** – 3 agentów (Herbal Guide, Support, Content), z multi-agent orchestration i retrieverem danych.
- **Admin Panel** – panel do zarządzania produktami, treściami, zamówieniami i użytkownikami z kontrolą ról (Admin, Editor, Logistics).

---

## 🚀 Technologie

- **Frontend:** Next.js, React, Tailwind CSS, react-i18next, Headless UI
- **Backend:** NestJS, TypeORM, PostgreSQL, JWT, bcrypt, class-validator
- **AI Integration:** Flowise, OpenAI API / lokalne LLM, Vector DB (np. ChromaDB)
- **CMS / Content:** Własny moduł CMS w NestJS (opcjonalnie Strapi)
- **Payments:** Stripe z obsługą Przelewy24 (PL), tokenizacja, PCI compliant
- **Notifications:** Nodemailer / Mailchimp, WhatsApp link/API, Webhooks
- **Deployment:** VPS (Ubuntu), Nginx, SSL (Let's Encrypt), Docker/PM2, GitHub Actions CI/CD

---

## 📁 Struktura Projektu

```
olejklonowski/
├── frontend/             # Next.js app
│   ├── pages/            # Routing
│   ├── components/       # UI components
│   ├── styles/           # Tailwind configuration
│   ├── i18n/             # Translation files
│   └── public/           # Static assets
│
├── backend/              # NestJS app
│   ├── src/
│   │   ├── modules/      # products, users, orders, ai, content
│   │   ├── auth/         # JWT logic
│   │   ├── common/       # DTOs, pipes, guards
│   │   └── main.ts       # Entry point
│   └── prisma/           # (jeśli używany Prisma zamiast TypeORM)
│
├── nginx/                # Reverse proxy config
├── docker/               # Dockerfiles, Compose
├── scripts/              # Deployment / maintenance
└── README.md             # Ten plik
```

---

## 🧠 AI Agenci (Flowise)

- **Herbal Guide Agent** – chatbot dla klientów, doradzający oleje i rytuały, z retrieverem po produktach i artykułach
- **Customer Support Agent** – śledzenie zamówień, polityki, FAQ (integracja z API zamówień)
- **Content Agent** – pomoc w tworzeniu postów na bloga, opisy produktów, social copy – dostępny w panelu admina
- **Supervisor Agent** – zarządza rozmowami i deleguje pytania do właściwego agenta (multi-agent orchestration)

---

## 🛒 Funkcje E-commerce

- Katalog produktów z filtrami i wyszukiwarką
- Strony produktu z narracją, zdjęciami, i sekcją "często kupowane razem"
- Koszyk z podsumowaniem i zarządzaniem stanem (React Context lub Redux)
- Checkout z obsługą konta i gościa, integracja Stripe (karty, Przelewy24)
- Subskrypcje, preordery, lokalny odbiór (opcjonalnie)

---

## 🛠 Panel Administracyjny

- Zarządzanie produktami, partiami, zdjęciami
- Zarządzanie zamówieniami: filtrowanie, aktualizacja statusów, śledzenie
- Blog i treści edukacyjne (editor WYSIWYG/Markdown)
- Role: Admin, Editor, Logistics
- Historia aktywności, eksport danych, GDPR tools (usuwanie, eksport)

---

## 📬 Powiadomienia i Messaging

- Maile transakcyjne: potwierdzenie zamówienia, wysyłki, zwroty
- Integracja z Mailchimp: zapisy, segmentacja, newsletter
- WhatsApp: link do czatu lub API z automatyzacją (w przyszłości)
- Webhooki: do Slacka, CRM, automatyzacji

---

## 🔒 Bezpieczeństwo & RODO

- HTTPS (Let's Encrypt + Nginx)
- JWT auth + hashowanie (bcrypt)
- Ograniczenia ról, logi aktywności adminów
- Ochrona przed atakami (rate limiting, CSRF, XSS, SQLi)
- GDPR-ready: eksport/usuwanie danych, minimalizacja danych, dobrowolna zgoda

---

## 🌍 Przyszłościowość

- Obsługa wielu języków (Next.js i18n-ready, tłumaczenia w CMS/DB)
- Możliwość integracji marketplace (Etsy, Amazon) i POS
- Skalowalna architektura (NestJS microservices-ready, frontend SSR/static)
- Mobile-ready (PWA, możliwość integracji z React Native)
- AI retrain workflows, nowe agenty (np. kreator receptur)

---

## ⚙️ Deployment

- VPS-y: osobne dla frontend i backend
- Docker/PM2, reverse proxy: Nginx
- CI/CD: GitHub Actions (testy + automatyczny deploy przez SSH)
- Backupy: bazy danych i uploads (szyfrowane)
- Monitoring: logi, uptime checkery, alerty błędów

---

## 📎 Kontakt i Licencja

Projekt prowadzony przez rodzinę Klonowskich. Domena: **olejklonowski.pl** Licencja: **Proprietary / Internal Use Only** (do wewnętrznego użytku marki Olej Klonowski)

---

> *"Niech technologia stanie się narzędziem harmonii. Olej Klonowski to więcej niż sklep – to dom dla duszy szukającej zdrowia w naturze."*

