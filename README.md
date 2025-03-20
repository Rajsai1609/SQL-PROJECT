# SQL-Based Hospital Managment System.
# Hospital Managment system using SQL-PROJECT
# CREATE EVERGREEN HOSPITAL DATA BASE WITH THE  CREATION OF TABLES , DOCTORS, PATEINTS , APPOINTMENTS , invoices. 
-- 1. Create a database and switch to it
CREATE DATABASE IF NOT EXISTS Evergreen_hospital_db;
USE Evergreen_hospital_db;

-- 2. Create doctors table
CREATE TABLE doctors (
    doctor_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    specialty VARCHAR(50),
    phone VARCHAR(20),
    email VARCHAR(50)
);

-- 3. Create patients table
CREATE TABLE patients (
    patient_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    age INT,
    gender VARCHAR(10),
    phone VARCHAR(20),
    address VARCHAR(100)
);

-- 4. Create appointments table
CREATE TABLE appointments (
    appointment_id INT PRIMARY KEY AUTO_INCREMENT,
    doctor_id INT NOT NULL,
    patient_id INT NOT NULL,
    appointment_date DATE NOT NULL,
    appointment_time TIME,
    reason VARCHAR(100),
    CONSTRAINT fk_doctor
        FOREIGN KEY (doctor_id)
        REFERENCES doctors (doctor_id)
        ON DELETE CASCADE
        ON UPDATE CASCADE,
    CONSTRAINT fk_patient
        FOREIGN KEY (patient_id)
        REFERENCES patients (patient_id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);
-- Create the invoices table
CREATE TABLE invoices (
    invoice_id INT PRIMARY KEY AUTO_INCREMENT,
    appointment_id INT NOT NULL,
    invoice_date DATE NOT NULL,
    total_amount DECIMAL(10, 2) NOT NULL,
    payment_method VARCHAR(20),
    payment_status VARCHAR(20),
    CONSTRAINT fk_appointment
        FOREIGN KEY (appointment_id)
        REFERENCES appointments (appointment_id)
        ON DELETE CASCADE
        ON UPDATE CASCADE
);
-- 5. Describe each table to verify structure
DESCRIBE doctors;
DESCRIBE patients;
DESCRIBE appointments;
DESCRIBE INVOICES;

                                 PART - 2 WORK               

--HOW TO INSERT A DATA VALUES IN EACH TABLE Doctors, Patients, appointments 
-- Make sure you're in the correct database
USE Evergreen_hospital_db;

-- 1. Insert data into doctors table

INSERT INTO doctors (name, specialty, phone, email)
VALUES
    ('Dr. Alice Smith', 'Pediatrics', '555-1000', 'alice.smith@hospital.org'),
    ('Dr. Bob Johnson', 'Cardiology', '555-2000', 'bob.johnson@hospital.org'),
    ('Dr. Emily Thompson', 'Neurology', '555-3000', 'emily.thompson@hospital.org'),
    ('Dr. John Adams', 'Orthopedics', '555-4000', 'john.adams@hospital.org'),
    ('Dr. Sarah Carter', 'Dermatology', '555-5000', 'sarah.carter@hospital.org'),
    ('Dr. Kevin White', 'Oncology', '555-6000', 'kevin.white@hospital.org'),
    ('Dr. Linda Nguyen', 'Ophthalmology', '555-7000', 'linda.nguyen@hospital.org');

-- 2. Insert data into patients table
INSERT INTO patients (name, age, gender, phone, address)
VALUES
    ('John Doe', 30, 'Male', '555-3000', '123 Main St'),
    ('Jane Doe', 28, 'Female', '555-4000', '456 Oak Ave'),
    ('Christopher Martin', 45, 'Male', '555-8000', '789 Pine Drive'),
    ('Emily Davis', 52, 'Female', '555-9000', '101 Maple Lane'),
    ('Michael Johnson', 35, 'Male', '555-1100', '202 River Rd'),
    ('Laura Brown', 42, 'Female', '555-1200', '303 Hillside St'),
    ('Robert Wilson', 38, 'Male', '555-1300', '404 South Blvd');

-- 3. Insert data into appointments table
INSERT INTO appointments (doctor_id, patient_id, appointment_date, appointment_time, reason)
VALUES
    (1, 1, '2025-03-20', '09:00:00', 'Regular Checkup'),
    (2, 2, '2025-03-30', '14:30:00', 'Cardiac Screening'),
    (3, 3, '2025-04-05', '10:15:00', 'Neurological Screening'),
    (4, 4, '2025-04-10', '13:00:00', 'Knee Pain Evaluation'),
    (5, 5, '2025-04-12', '15:45:00', 'Skin Rash Checkup'),
    (6, 6, '2025-04-15', '11:00:00', 'Cancer Follow-up'),
    (7, 7, '2025-04-18', '08:30:00', 'Vision Consultation');


  4.  Insert data  into the invoices table
INSERT INTO invoices (appointment_id, invoice_date, total_amount, payment_method, payment_status)
VALUES
    (1, '2025-03-21', 100.00, 'Cash', 'Paid'),
    (2, '2025-03-31', 250.00, 'Credit', 'Pending'),
    (3, '2025-04-06', 300.00, 'Insurance', 'Paid'),
    (4, '2025-04-11', 150.00, 'Cash', 'Paid'),
    (5, '2025-04-13', 200.00, 'Credit', 'Pending'),
    (6, '2025-04-16', 400.00, 'Insurance', 'Pending'),
    (7, '2025-04-19', 180.00, 'Cash', 'Paid');



--. Verify the data
SELECT * FROM doctors;
SELECT * FROM patients;
SELECT * FROM appointments;
SELECT * FROM invoices;


























































