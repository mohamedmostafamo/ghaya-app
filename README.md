# GHAYA (غاية) — Cloud Task Manager

A cloud-based task management web app built for the **Cloud Computing** course.
Users create an account, manage their tasks, and access the same data from any device.

🌐 **Live demo:** https://ghaya-app-670bc.web.app

## Features
- Sign up / log in with Email & Password or Google
- Add, edit, complete, and delete tasks (category, priority, date, time)
- Dashboard with live statistics, daily streak, and charts
- Calendar view, search, and category filters
- Arabic / English interface and dark / light theme
- Real-time sync across devices
- Each user can only access their own data

## Cloud Architecture
| Service | Role |
|---|---|
| **Firebase Authentication** | User accounts and sign-in |
| **Cloud Firestore** | Cloud NoSQL database (`users/{uid}/tasks`), region `eur3` |
| **Firebase Hosting** | Global hosting with HTTPS |
| **GitHub** | Source code and version control |

```
Browser ──► Firebase Hosting (index.html)
   │
   ├──► Firebase Authentication (who is the user?)
   └──► Cloud Firestore (user's tasks, protected by Security Rules)
```

Cloud concepts covered: BaaS / Serverless, SaaS delivery, scalability, high availability (multi-region database), access control (Security Rules), and CDN hosting.

## Tech Stack
HTML, CSS (Tailwind), JavaScript, Chart.js, Firebase (Auth, Firestore, Hosting)

## Security Rules
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
  }
}
```

## Run Locally
1. Clone the repository.
2. Open `public/index.html` with a local server (e.g. VS Code **Live Server**).

## Deploy
```
firebase login
firebase deploy --only hosting
```

## Author
Mohamed Mostafa — Cloud Computing Project 2026
