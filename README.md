# Tygers Sports Club Database

## Overview
The Tygers Club is a local community-based sports club that provides various sports and training programs to its members. 
This database project was designed to replace their outdated manual methods—such as paper files and spreadsheets—with a centralized,
efficient system to manage members, payments, training sessions, and coach assignments. 

## Objectives
*   Eliminate data duplication and prevent errors that could jeopardize sensitive club information.
*   Provide a singular, reliable system to effortlessly track payments and manage training schedules.
*   Ensure the database is straightforward and easy to navigate for users with limited technical knowledge.

## Technical Stack & Architecture
*   **Database Management System:** Designed for implementation on SQL Server 2019 or later.
*   **Data Integrity:** The database design is normalized to the Third Normal Form (3NF) to minimize redundancy and prevent update anomalies.
*   **File Organization:** Utilizes a primary data file (.mdf) for schema and a transaction log file (.ldf) for recovery,
*    with the potential for secondary files (.ndf) if the club expands

## Database Schema (Core Tables)
*   **Members**: Stores club members' personal information and join data.
*   **Coaches**: Holds details about the club's coaching staff, including their contact information and specialties.
*   **Teams**: Represents groups of players and links them to their assigned coach.
*   **Sessions**: Logs scheduled training exercises, including dates, times, locations, and the assigned coach.
*   **Payments**: Records financial transactions, ensuring amounts are greater than zero using a CHECK constraint.
*   **Registrations**: Acts as a bridge table to resolve the many-to-many relationship between Members and Sessions.

## Programmability & Database Objects
*   **Stored Procedures**: Includes `sp_AddMember`, `sp_ScheduleSession`, `sp_ProcessPayment`, and `sp_GetMemberSessions` to handle complex logic, data insertion, and input validation.
*   **Views**: Utilizes views like `vw_MemberDetails`, `vw_UpcomingSessions`, and `vw_PaymentSummary` to securely display grouped and joined data.
*   **Triggers**: Implements `trg_AfterPayment`, which automatically runs after a payment is inserted to log the transaction into a `PaymentAudit` table.
*   **Indexes**: Employs non-clustered indexes on frequently searched fields, such as `FirstName` and `LastName` in the Members table,
*    and `SessionDate` in the Sessions table, to enhance query performance.

## Security & Access Control
The system implements role-based access control with distinct permissions:
*   **Administrator**: Granted full select, insert, update, and delete access across all tables.
*   **Coach**: Granted read/write access restricted to the Sessions and Teams tables.
*   **Member**: Granted read-only access strictly limited to their own records via specified views.

## Project Contributors
*   Sinoyolo Calata
*   Marco Groenewald
*   Vhonani Sidogi
*   Cathrine Mpebe
