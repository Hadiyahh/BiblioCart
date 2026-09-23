# 📚 BiblioCart

### Full-Stack Bookstore & Inventory Management Platform

BiblioCart is a full-stack bookstore application built with **React, ASP.NET/C#, and SQL Server**.

The platform supports complete customer shopping workflows — including account management, cart operations, checkout, wishlists, coupons, recommendations, order history, and pre-orders — alongside administrative inventory-management functionality.


<img width="927" height="448" alt="BiblioCart bookstore homepage" src="https://github.com/user-attachments/assets/3a9f2c6f-1eca-4b8e-826a-8107d4107df6" />

---

## 🎯 Overview

BiblioCart was designed as a functional online bookstore with separate customer and administrator workflows.

The application evolved across two Agile development sprints:

- **Sprint 1** focused on the core bookstore functionality using C# and the initial UI implementation.
- **Sprint 2** expanded the application with a React frontend, additional customer features, improved UI/UX, and more complete administrative functionality.

The final architecture connected the React frontend to a C#/.NET backend and a shared SQL Server database. 

---

## ✨ Features

### 👤 Customer Features

Customers can:

- Create an account
- Log in and log out
- Browse available books
- Add and remove books from the shopping cart
- Update cart quantities
- Complete the checkout workflow
- Enter and validate shipping information
- Apply discount coupons
- Add books to a wishlist
- Move books from the wishlist to the cart
- View previous orders
- Pre-order out-of-stock books
- Receive genre-based book recommendations
- View account and profile information
- Switch between light and dark themes

---

### 🛒 Shopping & Checkout

BiblioCart supports a multi-step shopping workflow:

```text
Browse Books
     ↓
Add to Cart
     ↓
Review Cart
     ↓
Checkout
     ↓
Validate Shipping Information
     ↓
Apply Coupon (Optional)
     ↓
Calculate Final Total
     ↓
Place Order
     ↓
Order History
```

Checkout validation includes handling missing fields, invalid address formats, and shipping-cost calculations.

---

### ❤️ Wishlist

Authenticated customers can:

- Add books to their wishlist
- Remove books from their wishlist
- Move books from the wishlist into their cart
- Preserve pre-order status when applicable

The wishlist functionality was tested against duplicate additions, unauthenticated access, cart transfers, and pre-order behaviour.

---

### 📖 Recommendations

BiblioCart includes a lightweight **genre-based recommendation system**.

Recommendations can update based on the genres of books currently in the user's cart while still providing book suggestions when no cart history is available.

The team intentionally selected a simpler genre-based approach instead of a more complex recommendation engine so the feature remained achievable within the project timeline.

---

### 🛠️ Administrator Features

Administrators have access to management functionality for bookstore operations.

Admin capabilities include:

- Administrator authentication
- Inventory management
- Add / edit / remove books
- Manage book categories
- Manage suppliers
- Manage coupons and discounts
- Manage users
- Manage orders
- Validate related database records before deletion
- Access administrative dashboard functionality

---

## 🏗️ Architecture

BiblioCart follows a layered architecture:

```text
┌──────────────────────────────┐
│       React Frontend         │
│                              │
│ Catalog • Cart • Checkout    │
│ Wishlist • Profile • Admin   │
└──────────────┬───────────────┘
               │
               │ HTTP / REST
               ▼
┌──────────────────────────────┐
│      ASP.NET / C# API        │
│                              │
│ Controllers + Validation     │
│ Business Workflow Routing    │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│      Data Access Layer       │
│                              │
│ Typed Queries + DB Logic     │
└──────────────┬───────────────┘
               │
               ▼
┌──────────────────────────────┐
│        SQL Server            │
│                              │
│ Users • Books • Orders       │
│ Cart • Coupons • Wishlist    │
└──────────────────────────────┘
```

The application separates UI, API, database-access, and persistence responsibilities so each layer can evolve independently. DTOs and models are used to shape data passed between layers instead of exposing raw database rows directly to the frontend. :contentReference[oaicite:2]{index=2}

---

## 🛠️ Tech Stack

| Area | Technology |
|---|---|
| **Frontend** | React, TypeScript / JavaScript |
| **Backend** | C#, ASP.NET |
| **Database** | SQL Server |
| **API Testing** | Swagger |
| **Backend Testing** | MSTest |
| **Frontend Testing** | React Testing Library |
| **Version Control** | Git, GitHub |
| **Project Management** | Azure DevOps |
| **Development Environment** | Visual Studio / VS Code |

---

## 🧩 System Design

The project uses several object-oriented design principles.

### Layered Separation

```text
Frontend
   ↓
Controllers
   ↓
Data Access Layer
   ↓
SQL Server
```

This keeps:

- database logic out of the UI,
- request handling separate from persistence,
- frontend components focused on presentation and interaction, and
- database operations centralized in the DAL.

### Models & DTOs

DTOs and models are used to transfer structured data between system layers rather than directly exposing SQL records.

### User Roles

Customers and administrators share authentication concepts but follow different application workflows and permissions.

### Domain Relationships

Examples include:

- carts containing multiple items,
- orders containing multiple order entries,
- books belonging to categories,
- books associated with suppliers, and
- customers maintaining wishlists and order histories.

---

## 🧪 Testing

Testing was a major part of BiblioCart's development.

The project used:

- **Test-Driven Development (TDD)**
- **Black-box testing**
- **White-box testing**
- **Equivalence partitioning**
- **Backend unit testing**
- **React component testing**
- **API-interaction testing**

Sprint 1 primarily used C# test suites, while Sprint 2 introduced React Testing Library for frontend components and API behavior. :contentReference[oaicite:3]{index=3}

### Example Tested Workflows

Testing covered areas such as:

- account authentication
- cart additions and removals
- duplicate cart items
- checkout validation
- shipping information
- coupon application
- wishlist behavior
- recommendation updates
- unauthenticated access
- order processing
- admin CRUD operations

### Example Checkout Cases

```text
Empty checkout form
        ↓
Order rejected + validation shown

Invalid address
        ↓
Order rejected + error shown

Valid address
        ↓
Continue checkout

Express shipping
        ↓
Shipping fee included

Standard shipping
        ↓
No additional shipping fee
```

The project report documents passing black-box and white-box scenarios for several of these workflows. :contentReference[oaicite:4]{index=4}

---

## 🔄 Development Process

BiblioCart was developed across two structured Agile sprints using a combination of **Scrum** and **Extreme Programming (XP)**.

### Scrum Practices

The team used:

- user stories
- acceptance criteria
- product and sprint backlogs
- business-value prioritization
- effort estimation
- sprint planning
- twice-weekly stand-ups
- sprint reviews
- burndown charts
- Azure DevOps task tracking

### XP Practices

Engineering practices included:

- Test-Driven Development
- pair programming
- frequent refactoring
- continuous integration
- short development increments
- code review

Development followed a branching workflow where feature work was completed on separate branches and reviewed through pull requests before being merged. :contentReference[oaicite:5]{index=5}

---

## 🚀 Project Evolution

### Sprint 1 — Core Functionality

Sprint 1 focused on creating the initial working bookstore foundation.

Implemented areas included:

- customer account creation
- authentication
- logout
- shopping cart logic
- checkout
- basic admin permissions
- database integration
- unit testing
- initial administrative functionality

### Sprint 2 — Expansion & React Migration

Sprint 2 expanded the project into a more complete bookstore application.

Major additions included:

- React frontend migration
- wishlist
- coupon system
- order history
- pre-orders
- genre-based recommendations
- improved admin functionality
- UI refinements
- light/dark themes
- additional API integration
- React Testing Library tests


---

## 🖼️ Screenshots

### Book Catalogue
<img width="463" height="227" alt="image" src="https://github.com/user-attachments/assets/67ea22ed-1835-447d-9581-5214eff6e9f2" />


### Shopping Cart / Checkout

<img width="757" height="436" alt="image" src="https://github.com/user-attachments/assets/d70391c2-2837-44ad-9acf-71f1d5d3f6c5" />



This was a collaborative team project. Individual feature ownership varied across the two development sprints.

---

## 📁 Repository Structure

```text
BiblioCart/
├── BookStoreGUI/
│   └── Original C# / UI implementation
│
├── BookStoreLIB/
│   ├── Domain logic
│   ├── Data access
│   └── Tests
│
├── BookStoreReact/
│   └── bookstorereact.client/
│       └── src/
│           ├── components/
│           ├── pages/
│           └── tests/
│
├── TempTests/
├── BookStore.sln
└── README.md
```

---

## 🚀 Running Locally

> **Note:** BiblioCart was developed in a university course environment using a shared remote SQL Server database. Some original database credentials and environment-specific configuration are not included in the public repository.

### Requirements

- .NET SDK
- Node.js / npm
- SQL Server access or compatible local configuration
- Visual Studio or VS Code

### Backend

Configure the required database connection settings or environment variables.

Then run:

```bash
dotnet run
```

The ASP.NET backend exposes its API endpoints and Swagger interface.

### Frontend

Navigate to the React client:

```bash
cd BookStoreReact/bookstorereact.client
npm install
npm run dev
```

Depending on the configuration used in the repository, the frontend start command may also be:

```bash
npm start
```

Ensure the React API base URL points to the running ASP.NET backend.

---

## ⚠️ Project Scope

BiblioCart was developed as an academic software-engineering project rather than a commercial e-commerce system.

The primary goals were to practice:

- Agile software development
- Scrum planning
- Extreme Programming
- Test-Driven Development
- object-oriented design
- frontend/backend integration
- relational database development
- collaborative Git workflows

The project prioritizes functional software, iterative development, and engineering-process practice rather than production-scale deployment or performance optimization. :contentReference[oaicite:7]{index=7}

---

## 🔮 Future Improvements

Potential extensions include:

- Cloud deployment
- CI/CD pipeline
- Production authentication and authorization
- Payment-gateway integration
- Advanced recommendation algorithms
- Pagination for large catalogues
- Improved search and filtering
- Admin analytics and reporting
- Performance optimization
- Expanded automated testing
- Production database configuration



---

## 🎓 Project Context

**Course:** COMP 4220 — Agile Software Development  
**University:** University of Windsor  
**Term:** Fall 2025  
**Instructor:** Dr. Xiaobu Yuan

BiblioCart was created to apply Agile concepts in a realistic software-development environment through two full development sprints.

---

## 📚 Documentation

Additional academic documentation was created for the project, including:

- Final project report
- Sprint planning evidence
- User stories and acceptance criteria
- Black-box and white-box test cases
- TDD evidence
- Scrum / XP documentation
- Burndown charts
- [Project Presentation]([docs/BiblioCart-Presentation.pdf](https://canva.link/bdcydtwfxmakkqo))

<!-- If you add the files to docs/ later:

- [Final Project Report](docs/BiblioCart-Final-Report.pdf)

-->

---

## ⚠️ Disclaimer

BiblioCart is an educational prototype.

The checkout and payment workflows simulate e-commerce functionality and do **not** process real financial transactions.
