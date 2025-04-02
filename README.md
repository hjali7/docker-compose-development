# 🐳 docker-compose-development

یک پروژه‌ی چندسرویسی یکپارچه با Docker Compose شامل:
- **Frontend**: React (Vite) + Nginx
- **Backend**: Node.js + Go (هر دو فعال و قابل استفاده)
- **Database**: PostgreSQL

---

## 📐 معماری پروژه

```text
┌────────────────────────────┐
│        client-react        │◄────────────┐
└────────────────────────────┘             │
                                           │
┌────────────┐   ┌─────────────────────┐   │
│  api-node  │◄──┤      PostgreSQL     │◄──┘
└────────────┘   └─────────────────────┘
       ▲
       │
┌────────────┐
│ api-golang │
└────────────┘
```

---

## ⚙️ پیش‌نیازها

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

---

## 🚀 اجرای پروژه

در ترمینال، در مسیر پروژه:

```bash
docker-compose up --build
```

> این دستور تمام سرویس‌ها رو build و اجرا می‌کنه.

---

## 🌐 سرویس‌ها و پورت‌ها

| سرویس                | توضیح                          | پورت لوکال         |
|----------------------|----------------------------------|---------------------|
| client-react-vite    | حالت توسعه React + Vite         | http://localhost:5173 |
| client-react-nginx   | حالت build نهایی React با Nginx | http://localhost    |
| api-node             | REST API با Node.js              | http://localhost:3000 |
| api-golang           | REST API با Golang               | http://localhost:8080 |
| PostgreSQL           | دیتابیس پروژه                   | `localhost:5432`    |

---

## 🧪 توسعه و Debug

- برای توسعه React:
  ```bash
  cd client-react
  npm install
  npm run dev
  ```

- برای توسعه Node:
  ```bash
  cd api-node
  npm install
  npm run dev
  ```

- برای توسعه Go:
  از Docker استفاده شده و فایل‌ها mount شدن. می‌تونی مستقیماً تغییر بدی و دوباره build کنی.

---

## 🛢️ دیتابیس

- ایمیج: `postgres:15.1-alpine`
- یوزر پیش‌فرض: `postgres`
- پسورد: `foobarbaz`
- دیتابیس: `postgres`

اتصال برای هر دو API از طریق آدرس `db:5432` انجام می‌گیره (شبکه داخلی Docker).

---

## 👥 مشارکت

خوشحال می‌شم اگر پیشنهاد، ایراد یا Pull Request داری!  
برای ارتباط مستقیم: [hjali7](https://github.com/hjali7)

---

## 📁 ساختار پوشه‌ها

```
├── api-node          # Backend با Node.js
├── api-golang        # Backend با Golang
├── client-react      # فرانت‌اند React + Vite
├── docker-compose.yml
└── README.md
```