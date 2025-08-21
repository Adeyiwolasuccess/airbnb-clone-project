# Airbnb Clone Project

## 🚀 Overview
The **Airbnb Clone Project** is a backend-driven web application designed to replicate the core functionalities of Airbnb. It focuses on building a robust, scalable system that manages users, property listings, bookings, payments, and reviews. This project provides learners with real-world experience in full-stack development, backend architecture, and collaborative workflows.

---

## 🏆 Project Goals
- **User Management**: Secure registration, authentication, and profile management.  
- **Property Management**: Create, update, retrieve, and delete property listings.  
- **Booking System**: Implement reservation functionality with check-in/check-out details.  
- **Payment Processing**: Handle transactions and maintain payment records.  
- **Review System**: Enable users to leave reviews and ratings.  
- **Data Optimization**: Efficient data retrieval with indexing and caching.  

---

## ⚙️ Technology Stack
- **Backend Framework**: Django & Django REST Framework  
- **Database**: PostgreSQL  
- **API Standards**: REST (OpenAPI) & GraphQL  
- **Task Queue**: Celery  
- **Caching & Session Management**: Redis  
- **Containerization**: Docker  
- **CI/CD**: GitHub Actions (or other pipelines)  

---

## 👥 Team Roles
- **Backend Developer** – Build API endpoints, business logic, and models.  
- **Database Administrator (DBA)** – Design schema, indexing, and optimization.  
- **DevOps Engineer** – Handle deployment, monitoring, and scaling.  
- **QA Engineer** – Test and validate all functionalities.  

---

## 📚 Learning Objectives
By working on this project, learners will:  
- Master **GitHub collaborative workflows**.  
- Deepen knowledge of **backend architecture & relational databases**.  
- Implement **API security measures**.  
- Gain experience in **CI/CD pipeline automation**.  
- Explore integration of **Django, PostgreSQL, Redis, GraphQL, and Docker**.  

---

## ✅ Requirements
To participate in this project, learners should have:  
- A **GitHub account**.  
- Familiarity with **Markdown syntax**.  
- Experience with **Django** and **relational databases** (PostgreSQL/MySQL).  
- Understanding of **software development lifecycle** practices.  
- Comfort with modern tools like **Docker** and **GitHub Actions**.  

---

---

## 🗄️ Database Design

The database is designed to capture all core entities of the Airbnb Clone and their relationships, ensuring efficient storage and retrieval.

### Key Entities

#### 1. Users
- **id** (Primary Key)  
- **username** (Unique, String)  
- **email** (Unique, String)  
- **password_hash** (String, secured)  
- **date_joined** (Timestamp)  

**Relationships**:  
- A user can own multiple **properties**.  
- A user can make multiple **bookings**.  
- A user can write multiple **reviews**.  

---

#### 2. Properties
- **id** (Primary Key)  
- **owner_id** (Foreign Key → Users.id)  
- **title** (String)  
- **description** (Text)  
- **price_per_night** (Decimal)  

**Relationships**:  
- A property belongs to one **user** (owner).  
- A property can have multiple **bookings**.  
- A property can have multiple **reviews**.  

---

#### 3. Bookings
- **id** (Primary Key)  
- **user_id** (Foreign Key → Users.id)  
- **property_id** (Foreign Key → Properties.id)  
- **check_in_date** (Date)  
- **check_out_date** (Date)  

**Relationships**:  
- A booking belongs to one **user**.  
- A booking belongs to one **property**.  
- A booking can have one related **payment**.  

---

#### 4. Payments
- **id** (Primary Key)  
- **booking_id** (Foreign Key → Bookings.id)  
- **amount** (Decimal)  
- **payment_status** (Enum: pending, completed, failed)  
- **timestamp** (Timestamp)  

**Relationships**:  
- A payment is linked to one **booking**.  

---

#### 5. Reviews
- **id** (Primary Key)  
- **user_id** (Foreign Key → Users.id)  
- **property_id** (Foreign Key → Properties.id)  
- **rating** (Integer: 1–5)  
- **comment** (Text)  

**Relationships**:  
- A review is written by one **user**.  
- A review is linked to one **property**.  

---

### 🔗 Entity Relationships Summary
- **User – Property**: One-to-Many (a user can own many properties).  
- **User – Booking**: One-to-Many (a user can book many properties).  
- **User – Review**: One-to-Many (a user can write many reviews).  
- **Property – Booking**: One-to-Many (a property can have many bookings).  
- **Property – Review**: One-to-Many (a property can have many reviews).  
- **Booking – Payment**: One-to-One (each booking has one payment record).  

---
