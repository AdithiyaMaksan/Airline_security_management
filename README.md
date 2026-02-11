
# Airline Security Management System

## 📋 Overview
This is a DBMS-based project designed to simulate a full-fledged airline security and reservation management system. It uses SQL and PL/SQL to manage airports, airlines, flights, passengers, tickets, and employee data.

---

## 💾 Tech Stack
- **SQL (Oracle)**
- **PL/SQL Procedures**
- Normalized Database Design (3NF)
- ER & Schema Diagrams

---

## 📁 Project Structure

- `create_tables.sql` – All table creation scripts
- `insert_data.sql` – Data insertion scripts for tables
- `procedures.sql` – PL/SQL stored procedures
- `report_queries.sql` – Useful report generation queries
- `README.md` – Project documentation

---

## 📌 Main Features

- Manage **airports, airlines, and flights**
- Store **passenger and employee** data
- Handle **ticket bookings and cancellations**
- Normalize data to eliminate redundancy (up to **3NF**)
- Includes **PL/SQL procedures** for:
  - Economy passengers flying to DFW
  - Flights filtered by current status

---

## 📊 ER Diagram Highlights

Entities:
- City
- Airport
- Airline
- Flight
- Passenger
- Ticket
- Employee

Relationships:
- A city has one airport
- Airlines operate multiple flights
- Passengers book/cancel tickets
- Employees serve passengers

---

## 🚀 How to Run

1. Use **Oracle SQL Developer** or any compatible SQL platform.
2. Execute `create_tables.sql` to generate the schema.
3. Run `insert_data.sql` to populate the database.
4. Run `procedures.sql` to load stored procedures.
5. Test report queries via `report_queries.sql`.

---

## 👨‍💻 Sample PL/SQL Procedure

```
CREATE OR REPLACE PROCEDURE FLIGHTSBYSTATUS(IN_STATUS IN VARCHAR2) AS
  CURSOR fSTATUS IS
    SELECT DISTINCT F.FLIGHT_CODE, AL.AL_NAME, F.ARRIVAL, F.DEPARTURE,
           F.SOURCE, F.DESTINATION, F.STATUS, F.FLIGHTTYPE
    FROM AIRLINE AL, FLIGHT F
    WHERE AL.AIRLINEID = F.AIRLINEID AND F.STATUS = IN_STATUS;
  FlightStatus fSTATUS%ROWTYPE;
BEGIN
  OPEN fSTATUS;
  LOOP
    FETCH fSTATUS INTO FlightStatus;
    EXIT WHEN fSTATUS%NOTFOUND;
    DBMS_OUTPUT.PUT_LINE(FlightStatus.FLIGHT_CODE || ' ' || FlightStatus.AL_NAME);
  END LOOP;
  CLOSE fSTATUS;
END;
```

---

## 📌 Notes
- The system is **designed for international flights only**.
- Airports are **publicly owned commercial airports**.
- Data integrity is enforced using **foreign key constraints**.

---

## 📚 Credits
Created by: **Adithiya K**  
Institution: **Lovely Professional University**

---
