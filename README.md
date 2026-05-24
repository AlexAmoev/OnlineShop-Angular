# Laptop Shop — Angular Frontend

A fully functional e-commerce frontend for a laptop store, built with Angular.  
Browse products, filter by brand/category/price, manage your cart, and authenticate via a live API.

## 🚀 Live Demo

**[https://it-step-angular-final-project.vercel.app](https://it-step-angular-final-project.vercel.app)**

### Test Account

Register at [everrest.educata.dev](https://everrest.educata.dev) to get a test account for login/cart features.

---

## Tech Stack

- **Angular 17** — Frontend framework
- **TypeScript** — Language
- **RxJS / BehaviorSubject** — Reactive state management
- **Angular Reactive Forms** — Form handling and validation
- **HTTP Interceptor** — Automatic JWT token injection
- **Route Guards** — Protected routes for authenticated users
- **Vercel** — Deployment

---

## Features

- Product listing with pagination
- Filter by brand, category, price range, rating, and keyword
- Product detail page
- User registration and login via JWT
- Cart — visible only after login, only when items are added
- Checkout flow
- Profile page with update and password change
- Password recovery

---

## Project Structure

```
src/app/
├── home/           → Product listing with filters
├── brands/         → Brand filter component
├── filter/         → Advanced filter sidebar
├── cart/           → Shopping cart (auth-protected)
├── login/          → Login form
├── sing-up/        → Registration form
├── profile/        → User profile management
├── password-rec/   → Password recovery
├── navbar/         → Navigation with auth state
├── api.service.ts  → All HTTP calls in one service
├── auth.interceptor.ts → Auto JWT injection
└── page-block.guard.ts → Route protection
```

---

## Key Technical Details

**Auth Interceptor** — automatically attaches JWT token to every authenticated request:

```typescript
// auth.interceptor.ts
// Token is read from localStorage and injected into Authorization header
```

**Reactive State** — cart visibility and auth state managed via BehaviorSubject:

```typescript
private isCart = new BehaviorSubject<boolean>(false);
isCart$ = this.isCart.asObservable();
```

**Dynamic Search** — filters are built into query params only when set:

```typescript
Object.keys(filter).forEach((key) => {
  if (filter[key] !== "" && filter[key] !== null) {
    params[key] = filter[key];
  }
});
```

---

## Local Development

### Prerequisites

- Node.js 18+
- Angular CLI: `npm install -g @angular/cli`

### Setup

```bash
git clone https://github.com/AlexAmoev/OnlineShop-Angular.git
cd It-Step_Angular_Final_Project
npm install
ng serve
```

Open `http://localhost:4200`
