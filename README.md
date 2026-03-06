# MyNoteApp

A modern Android Notes application built with **Kotlin, Jetpack Compose, and Firebase**.
The app allows authenticated users to create, edit, and delete personal notes stored securely in **Firebase Firestore**.

---

## Overview

MyNoteApp is designed as a lightweight cloud-based note manager where each user has a private notes collection.
The project demonstrates a **clean Android architecture**, Firebase integration, and modern UI development with Jetpack Compose.

---

## Features

* User authentication with **Firebase Authentication**
* Create notes
* Edit existing notes
* Delete notes
* Secure per-user Firestore storage
* Modern UI using **Jetpack Compose**
* MVVM architecture
* Error handling and loading states

---

## App Flow

```text
Login / Register
       ↓
   Notes Screen
       ↓
Create / Edit Note
       ↓
Firestore Database
```

---

## Architecture

The project follows a **clean MVVM architecture**:

```text
UI (Compose Screens)
        ↓
ViewModel
        ↓
Repository
        ↓
Firebase Service
        ↓
Firestore Database
```

### Project Structure

```
com.mynoteapp

├── data
│   ├── firebase
│   ├── model
│   └── repository
│
├── navigation
│
├── ui
│   ├── components
│   └── screens
│
├── viewmodel
│
└── utils
```

---

## Technologies Used

| Technology              | Purpose                      |
| ----------------------- | ---------------------------- |
| Kotlin                  | Primary programming language |
| Jetpack Compose         | UI toolkit                   |
| Firebase Authentication | User authentication          |
| Firebase Firestore      | Cloud database               |
| ViewModel               | State management             |
| Kotlin Coroutines       | Asynchronous operations      |
| Navigation Compose      | Screen navigation            |

---

## Database Structure

Firestore structure used in this project:

```
users
   └── userId
        └── notes
              └── noteId
                    title
                    content
                    createdAt
                    updatedAt
```

Each user has their own isolated notes collection.

---

## Firestore Security Rules

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {

    match /users/{userId}/notes/{noteId} {
      allow read, write: if request.auth != null
      && request.auth.uid == userId;
    }

  }
}
```

These rules ensure that users can only access their own notes.

---

## Installation

### 1 Clone the repository

```
git clone https://github.com/YOUR_USERNAME/MyNoteApp.git
```

### 2 Open in Android Studio

Open the project in **Android Studio Hedgehog or newer**.

### 3 Add Firebase configuration

Place your Firebase configuration file inside:

```
app/google-services.json
```

### 4 Run the application

Connect a device or emulator and run the app.

---

## Firebase Setup

1. Go to **Firebase Console**
2. Create a new project
3. Add Android app with package name:

```
com.mynoteapp
```

4. Enable:

```
Authentication → Email/Password
Firestore Database
```

5. Download:

```
google-services.json
```

and place it in the **app/** folder.

---

## Screens

**Login Screen**
User authentication using Firebase.

**Notes Screen**
Displays user notes and allows note management.

**Add / Edit Note Screen**
Create or modify notes.

---

## Future Improvements

* Real-time Firestore updates
* Search notes
* Pin important notes
* Note categories
* Dark mode customization
* Offline note support

---

## Author

Developed as a learning and portfolio project demonstrating modern Android development practices.

---

## License

This project is open-source and available for educational purposes.
