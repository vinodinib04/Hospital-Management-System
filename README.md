# **Hospital Management System (HMS)**

## **Overview**
The Hospital Management System (HMS) is a web-based application designed to streamline hospital operations. It provides an intuitive interface for managing patients, doctors, appointments, billing, and other administrative tasks. This system improves efficiency and reduces the workload on hospital staff by automating routine processes.

## **Features**
- **Patient Management**: Register and manage patient details.
- **Doctor Management**: Store and manage doctor profiles and specialties.
- **Appointment Scheduling**: Book, update, and track appointments between patients and doctors.
- **Billing System**: Generate and track bills for services rendered.
- **Dashboard**: View hospital statistics and quick access to key functions.

## **Technologies Used**
### **Backend**
- **Flask (Python)**:
  - `Flask`: Core routing and request handling.
  - `Flask-MySQL`: For database integration.
  - `Flask-Login`: For user authentication and session management.

### **Frontend**
- **HTML, CSS, Bootstrap, JavaScript**

### **Database**
- **MySQL**

## **Database Schema**
### **Tables**
#### 1. Patients
| Column          | Type          | Constraints               |
|------------------|---------------|---------------------------|
| `id`            | INT           | Primary Key, AUTO_INCREMENT |
| `name`          | VARCHAR       | Required                  |
| `age`           | INT           |                           |
| `gender`        | VARCHAR       |                           |
| `contact_number`| VARCHAR       |                           |
| `address`       | VARCHAR       |                           |
| `admitted_date` | DATE          |                           |

#### 2. Doctors
| Column          | Type          | Constraints               |
|------------------|---------------|---------------------------|
| `id`            | INT           | Primary Key, AUTO_INCREMENT |
| `name`          | VARCHAR       | Required                  |
| `specialty`     | VARCHAR       |                           |
| `contact_number`| VARCHAR       |                           |
| `email`         | VARCHAR       | Unique                    |

#### 3. Appointments
| Column          | Type          | Constraints               |
|------------------|---------------|---------------------------|
| `id`            | INT           | Primary Key, AUTO_INCREMENT |
| `patient_id`    | INT           | Foreign Key references `Patients.id` |
| `doctor_id`     | INT           | Foreign Key references `Doctors.id` |
| `appointment_date` | DATE       |                           |
| `status`        | VARCHAR       |                           |

#### 4. Billing
| Column          | Type          | Constraints               |
|------------------|---------------|---------------------------|
| `id`            | INT           | Primary Key, AUTO_INCREMENT |
| `patient_id`    | INT           | Foreign Key references `Patients.id` |
| `appointment_id`| INT           | Foreign Key references `Appointments.id` |
| `amount`        | DECIMAL       |                           |
| `status`        | VARCHAR       |                           |
| `billing_date`  | TIMESTAMP     | Default: `CURRENT_TIMESTAMP` |

### **Relationships**
- **Patients to Appointments**: One-to-Many (each patient can have multiple appointments).
- **Doctors to Appointments**: One-to-Many (each doctor can have multiple appointments).
- **Appointments to Billing**: One-to-One (each appointment has one associated billing record).


