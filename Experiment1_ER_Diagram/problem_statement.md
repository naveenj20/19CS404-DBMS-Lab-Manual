# ER Diagram Workshop

# Name: Naveen Jaisanker
# Reg. No.: 212224110039
# Date: 16/05/2026

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

## Business Context
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

## Requirements
- Members register with name, membership type, and start date.
- Each member can join multiple programs (Yoga, Zumba, Weight Training).
- Trainers assigned to programs; a program may have multiple trainers.
- Members may book personal training sessions with trainers.
- Attendance recorded for each session.
- Payments tracked for memberships and sessions.

---

## ER Diagram

<img width="940" height="461" alt="image" src="https://github.com/user-attachments/assets/b3bb4ee9-5acf-4485-8299-dd0acfc1639c" />

---

## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| Member | **MemberID (PK)**, Name, MembershipType, StartDate | Stores gym member details |
| Program | **ProgramID (PK)**, ProgramName, Schedule, Duration | Stores fitness programs |
| Trainer | **TrainerID (PK)**, Name, Specialization, Experience | Stores trainer information |
| Session | **SessionID (PK)**, Date, Time, Type, MemberID (FK), TrainerID (FK) | Tracks personal/group sessions |
| Payment | **PaymentID (PK)**, Amount, PaymentDate, PaymentType, MemberID (FK) | Records payments |
| Attendance | **AttendanceID (PK)**, Status, Date, SessionID (FK) | Tracks attendance |
| Member_Program | **MemberID (FK)**, **ProgramID (FK)** | Junction table for Member–Program |
| Trainer_Program | **TrainerID (FK)**, **ProgramID (FK)** | Junction table for Trainer–Program |

---

## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Member ↔ Program | M:N | Partial | Members can join multiple programs |
| Trainer ↔ Program | M:N | Partial | Trainers can teach multiple programs |
| Member ↔ Trainer (via Session) | M:N | Partial | Members book sessions with trainers |
| Session ↔ Attendance | 1:N | Total on Attendance | Sessions have multiple attendance records |
| Member ↔ Payment | 1:N | Total on Payment | Members make multiple payments |
| Member ↔ Session | 1:N | Partial | One member attends many sessions |
| Trainer ↔ Session | 1:N | Partial | One trainer conducts many sessions |

---

## Assumptions
- A session is required for tracking attendance.
- Payments include memberships and personal sessions.
- Attendance is recorded per session.
- Programs may temporarily exist without trainers or members.

---

# Scenario B: City Library Event & Book Lending System

## Business Context
The Central Library wants to manage book lending and cultural events.

## Requirements
- Members borrow books, with loan and return dates tracked.
- Each book has title, author, and category.
- Library organizes events; members can register.
- Each event has one or more speakers/authors.
- Rooms are booked for events and study.
- Overdue fines apply for late returns.

---

## ER Diagram
<img width="940" height="628" alt="image" src="https://github.com/user-attachments/assets/0f472635-974a-42e5-8916-c151e768ce94" />

---

## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| Member | **MemberID (PK)**, Name, Email, Phone | Stores member details |
| Book | **BookID (PK)**, Title, Author, Category | Represents book copies |
| Loan | **LoanID (PK)**, LoanDate, ReturnDate, DueDate, MemberID (FK), BookID (FK) | Tracks borrowed books |
| Event | **EventID (PK)**, EventName, Date, Type, RoomID (FK) | Stores event details |
| Speaker | **SpeakerID (PK)**, Name, Expertise, Contact | Stores speaker information |
| Room | **RoomID (PK)**, RoomName, Capacity, Type | Represents library rooms |
| Fine | **FineID (PK)**, Amount, Status, LoanID (FK) | Tracks overdue fines |
| Member_Event | **MemberID (FK)**, **EventID (FK)** | Junction table for event registrations |
| Event_Speaker | **EventID (FK)**, **SpeakerID (FK)** | Junction table for speakers |
| Member_Room | **MemberID (FK)**, **RoomID (FK)** | Junction table for study room booking |

---

## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Member ↔ Book (via Loan) | 1:N | Total on Loan | Members borrow many books |
| Loan ↔ Fine | 1:1 | Partial | Fine generated only for overdue loans |
| Member ↔ Event | M:N | Partial | Members register for multiple events |
| Event ↔ Speaker | M:N | Total on Event | Events can have multiple speakers |
| Event ↔ Room | N:1 | Total on Event | Each event occurs in one room |
| Member ↔ Room | M:N | Partial | Members can book study rooms |
| Book ↔ Loan | 1:N | Total on Loan | One book can appear in many loans |

---

## Assumptions
- Each BookID represents one unique physical copy.
- Fine records are created only for overdue returns.
- Rooms can be reused at different times.
- No overlapping room bookings are allowed.
- Authors and speakers are treated as the same entity type.

---

# Scenario C: Restaurant Table Reservation & Ordering

## Business Context
A popular restaurant wants to manage reservations, food ordering, and billing.

## Requirements
- Customers can reserve tables or walk in.
- Each reservation includes date, time, and number of guests.
- Customers place food orders linked to reservations.
- Each order contains multiple dishes; dishes belong to categories.
- Bills generated per reservation, including service charges.
- Waiters assigned to serve reservations.

---

## ER Diagram
<img width="719" height="715" alt="image" src="https://github.com/user-attachments/assets/ece06ae3-8423-4960-932e-e2edc4c5cfa0" />

---

## Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| Customer | **CustomerID (PK)**, Name, PhoneNumber, Email | Stores customer information |
| Reservation | **ReservationID (PK)**, ReservationDate, ReservationTime, GuestCount, CustomerID (FK), TableID (FK), WaiterID (FK) | Tracks reservations |
| Table | **TableID (PK)**, TableNumber, Capacity, Status | Represents restaurant tables |
| Order | **OrderID (PK)**, OrderTime, TotalAmount, SpecialInstructions, ReservationID (FK) | Stores food orders |
| Dish | **DishID (PK)**, DishName, Description, Price, CategoryID (FK) | Represents menu items |
| Category | **CategoryID (PK)**, CategoryName | Dish categories |
| Waiter | **WaiterID (PK)**, Name, Shift, AssignedSection | Stores waiter details |
| Bill | **BillID (PK)**, TaxAmount, ServiceCharge, FinalTotal, PaymentStatus, ReservationID (FK) | Stores billing details |
| Order_Dish | **OrderID (FK)**, **DishID (FK)** | Junction table for Order–Dish |

---

## Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Customer ↔ Reservation | 1:N | Partial | Customers can make many reservations |
| Reservation ↔ Table | N:1 | Total on Reservation | One reservation assigned to one table |
| Reservation ↔ Order | 1:N | Total on Order | Multiple orders per reservation |
| Order ↔ Dish | M:N | Total on Order | Orders contain multiple dishes |
| Dish ↔ Category | N:1 | Total on Dish | Each dish belongs to one category |
| Waiter ↔ Reservation | 1:N | Partial | Waiters serve multiple reservations |
| Reservation ↔ Bill | 1:1 | Total on Bill | One bill generated per reservation |

---

## Assumptions
- Walk-in customers are treated as instant reservations.
- Dish prices are fixed at the time of ordering.
- Service charges are calculated during billing.
- Tables become occupied during active reservations.
- Tables become available after payment completion.

---
