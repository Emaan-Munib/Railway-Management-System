
# 🚆 Railway Management System

### ASP.NET Web Forms | C# | Microsoft SQL Server | Bootstrap

A database-driven **Railway Management and Online Ticket Booking System** developed using ASP.NET Web Forms, C#, and Microsoft SQL Server.

The application provides a web-based platform for passengers to explore railway schedules, book tickets, manage reservations, maintain personal profiles, submit reviews, and interact with a reward points system.

This project demonstrates **full-stack web application development, relational database design, SQL integration, session management, and event-driven programming**.

---

## 🌟 Key Features

### 🔐 User Authentication
- User registration and login
- Account validation using database records
- Session-based user identification
- Logout functionality
- Personal account management

### 🚉 Train & Schedule Management
- Browse available railway schedules
- Search trains by source and destination
- View departure dates and times
- Check available seats
- Explore train information and destinations

### 🎫 Ticket Booking
- Search available journeys
- Select travel dates
- Choose ticket classes
- Specify the number of passengers
- Book tickets through the web interface
- Update available seat counts following bookings

### 👤 User Profile
- View personal account information
- View booking history
- Cancel existing reservations
- Restore seat availability following cancellation
- Upload a profile image
- Track reward points

### ⭐ Reviews & Feedback
- Submit passenger reviews
- Store reviews in SQL Server
- Display previously submitted reviews
- Associate reviews with registered travellers

### 🎁 Reward Points
- Track points associated with passenger accounts
- Use reward points within the booking workflow
- Update points through database operations

---

## 🛠️ Technology Stack

| Category | Technologies |
|---|---|
| Backend | C#, ASP.NET Web Forms |
| Frontend | HTML, CSS, Bootstrap, ASP.NET Controls |
| Database | Microsoft SQL Server |
| Database Connectivity | ADO.NET, SqlClient |
| Authentication | ASP.NET Sessions, SQL Server |
| IDE | Microsoft Visual Studio |
| Web Server | IIS Express |
| Architecture | Event-driven, database-driven web application |

---

## 🏗️ Application Architecture

```text
                  Railway Management System
                             |
                    ASP.NET Web Forms
                             |
                +------------+------------+
                |                         |
          User Interface             C# Code-Behind
                |                         |
          HTML / CSS /                Business Logic
           Bootstrap                      |
                |                    ADO.NET / SqlClient
                |                         |
                +-------------------------+
                                          |
                                  Microsoft SQL Server
                                          |
                 +------------------------+--------------------+
                 |                        |                    |
              Traveller                Schedule              Booking
                 |                        |                    |
              Reviews                  Train Data          Reservations
                 |
             Reward Points
```

The application follows the ASP.NET Web Forms model, separating `.aspx` user interface files from their corresponding `.aspx.cs` code-behind files.

SQL Server stores and manages application data, while ADO.NET provides database connectivity.

---

## 📂 Project Structure

```text
Railway-Management-System/
|
|-- Railway Management System.sln
|
|-- Railway Management System/
|   |
|   |-- Default.aspx
|   |-- Main Page.aspx
|   |-- Login.aspx
|   |-- Sign Up.aspx
|   |-- Booking.aspx
|   |-- Profile.aspx
|   |-- Experience.aspx
|   |-- Reviews.aspx
|   |-- Reward System.aspx
|   |-- Staff.aspx
|   |-- About.aspx
|   |-- Contact.aspx
|   |
|   |-- *.aspx.cs
|   |-- *.aspx.designer.cs
|   |
|   |-- Content/
|   |-- Scripts/
|   |-- Images/
|   |
|   |-- Web.config
|   |-- packages.config
|   |-- Railway Management System.csproj
|
|-- SQLQuery1.sql
|-- README.md
|-- .gitignore
```

The structure above shows the main application files. Additional supporting assets and configuration files are included in the Visual Studio project.

---

## 🗄️ Database Design

The project uses **Microsoft SQL Server** to store railway information, passenger records, reservations, reviews, and reward points.

### Main Database Tables

| Table | Purpose |
|---|---|
| `Traveller` | Passenger account information |
| `Users` | User information and reward points |
| `Bookings` | Reservation information in the supplied SQL schema |
| `Schedule` | Railway routes, dates, times, and seat availability |
| `Experience` | Train names, stations, durations, and fares |
| `Staff` | Railway staff information |
| `TrainCategories` | Categories of trains |
| `TrainDetails` | Train descriptions and details |
| `Destinations` | Destination information |
| `TrainDestinations` | Train-to-destination relationships |
| `Reviews` | Passenger feedback |
| `RewardsRedemption` | Reward redemption records |

### Relational Database Concepts

The database design demonstrates:

- Primary keys
- Foreign keys
- Identity columns
- One-to-many relationships
- Many-to-many relationships
- Referential integrity
- SQL constraints
- Relational data modeling

### Database Operations

The C# application performs SQL operations using ADO.NET, including:

- `SELECT` for retrieving passenger and schedule information
- `INSERT` for account creation, reservations, and reviews
- `UPDATE` for seat availability and reward points
- `DELETE` for booking cancellation

Several application queries use SQL parameters to pass user-provided values.

**Database note:** The supplied SQL script and application code contain schema differences that require reconciliation before a clean database setup. See the limitations section.

---

## ⚙️ Installation & Setup

### Prerequisites

Install the following:

- Microsoft Visual Studio with ASP.NET and web development support
- .NET Framework compatible with the project
- Microsoft SQL Server
- SQL Server Management Studio (SSMS)
- IIS Express
- NuGet package restore support

### 1. Clone the Repository

```bash
git clone https://github.com/Emaan-Munib/Railway-Management-System.git
cd Railway-Management-System
```

### 2. Open the Visual Studio Solution

Open:

```text
Railway Management System.sln
```

Allow Visual Studio to load the project and restore missing NuGet packages.

### 3. Configure SQL Server

Open Microsoft SQL Server Management Studio.

Review the database script:

```text
SQLQuery1.sql
```

The supplied script contains table definitions and sample records.

Before executing it as a complete setup script, the database definitions need to be reconciled with the application's SQL queries.

In particular, the application references a `Booking` table, while the supplied script defines `Bookings`.

### 4. Update Database Connection

Open:

```text
Railway Management System/Web.config
```

Locate the connection string named `sqlCon1`.

Configure it for your local SQL Server instance and the database containing the required application tables.

Example:

```xml
<connectionStrings>
  <add name="sqlCon1"
       connectionString="Data Source=YOUR_SERVER;
                         Initial Catalog=YOUR_DATABASE;
                         Integrated Security=True;"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```

Replace the placeholders with your own SQL Server configuration.

### 5. Run the Application

1. Build the project in Visual Studio.
2. Start the application using IIS Express.
3. Open the application in your browser.
4. Register or log in to access passenger features.

**Note:** The project may require database schema corrections and environment-specific configuration before it runs successfully on a new machine.

---

## 🔄 Application Workflows

### User Registration & Login

```text
User Opens Application
          |
     Registration
          |
   Enter User Details
          |
  Validate Existing User
          |
  Insert Traveller Record
          |
       Login
          |
  Verify Credentials
          |
   Create User Session
          |
       Dashboard
```

### Ticket Booking

```text
      User Login
          |
     Search Routes
          |
    View Schedules
          |
    Select Journey
          |
    Choose Ticket Class
          |
   Enter Passenger Count
          |
     Book Journey
          |
    Update Available Seats
          |
     Save Reservation
```

### Booking Cancellation

```text
      User Profile
           |
     View Bookings
           |
    Select Reservation
           |
     Cancel Booking
           |
    Delete Booking Record
           |
    Restore Available Seats
```

---

## 💻 Application Modules

### 1. Home & Main Page

Provides the main entry point to the railway booking platform.

Users can explore available journeys and search for routes.

### 2. Registration & Login

Handles passenger account creation and authentication using C# and SQL Server.

### 3. Booking Module

Processes journey searches, ticket selection, passenger counts, reservations, and seat availability updates.

### 4. Profile Module

Displays traveller details, booking information, reward points, and profile images.

### 5. Reviews Module

Allows registered travellers to submit feedback and view passenger reviews.

### 6. Reward System

Provides reward-related functionality connected to traveller points.

### 7. Additional Pages

Includes train information, staff, contact, and about pages.

---

## 🎯 Learning Outcomes

This project demonstrates practical experience in:

- Developing dynamic websites using ASP.NET Web Forms
- Writing backend logic using C#
- Connecting web applications to SQL Server
- Designing relational database schemas
- Implementing CRUD operations
- Handling user sessions
- Creating data-driven user interfaces
- Managing reservation and seat availability workflows
- Integrating multiple application modules
- Working with Visual Studio solutions and NuGet packages

---

## ⚠️ Current Limitations

This is an academic development project and is not production-ready.

### Database Compatibility

The provided SQL script contains inconsistencies with the application code, including differences in table names, database names, and booking definitions.

The schema needs to be aligned with the application's queries before reliable deployment.

### Authentication Security

The current implementation stores and compares passwords as plaintext.

A production application should use secure password hashing and established authentication mechanisms.

### Booking Consistency

Booking insertion, seat availability changes, and reward point updates should be handled within database transactions to prevent partial updates.

### Configuration

The application uses a local SQL Server configuration that must be updated for each development environment.

### Deployment

The project is primarily configured for local execution through Visual Studio and IIS Express.

---

## 🚀 Future Improvements

Potential enhancements include:

- Secure password hashing and account authentication
- Role-based authorization for passengers and administrators
- Transaction-safe ticket booking and cancellation
- Improved database schema and migration scripts
- Seat allocation and reservation conflict prevention
- Payment gateway integration
- Email booking confirmations
- Ticket PDF generation
- Improved responsive design
- Automated integration and unit tests
- Deployment to IIS or a cloud hosting environment
- Migration to a modern ASP.NET Core architecture

---

## 📌 Project Status

**Academic Full-Stack Web Development & Database Management Project**

The project implements a railway booking application using ASP.NET Web Forms, C#, and SQL Server.

It demonstrates practical development of database-driven web application modules, including user management, reservation workflows, profile management, and customer feedback.

The existing implementation provides a foundation for further security, reliability, and deployment improvements.

---

## 📚 References

- [Microsoft ASP.NET Web Forms](https://learn.microsoft.com/en-us/aspnet/web-forms/)
- [Microsoft SQL Server](https://learn.microsoft.com/en-us/sql/sql-server/)
- [ADO.NET](https://learn.microsoft.com/en-us/dotnet/framework/data/adonet/)
- [Bootstrap](https://getbootstrap.com/)
- [Microsoft Visual Studio](https://visualstudio.microsoft.com/)
