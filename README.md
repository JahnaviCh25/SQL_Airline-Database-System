# **Flight Booking System – README**  

## **Project Overview**  
The **Flight Booking System** is a **database-driven project** designed to **streamline flight reservations** by managing passenger bookings, seat assignments, payment processing, and flight schedules efficiently. This system eliminates the inefficiencies of manual booking by utilizing **SQL databases** for **real-time flight availability, structured reservations, and seamless transactions**.  

## **Project Objectives**  

✅ **Centralized Flight Management:** Efficient handling of **flight schedules, passengers, bookings, and transactions**.  
✅ **Real-Time Reservation System:** Ensure up-to-date availability of **flights, seats, and services**.  
✅ **User-Friendly Passenger Booking:** Passengers can **book, modify, or cancel** their reservations easily.  
✅ **Secure Payment Processing:** Track transactions, manage refunds, and **ensure data security**.  
✅ **Automated Flight Reports:** Generate **real-time reports** on flight availability, booking trends, and revenue.  

---

## **System Scope & Functionalities**  

🔹 **Passenger Management** – Store and update passenger details, including reservations, travel history, and preferences.  
🔹 **Flight Scheduling & Booking** – Automate flight searches, booking confirmations, and cancellations.  
🔹 **Seat Assignments** – Allocate and manage seat reservations based on **travel class preferences**.  
🔹 **Payment Processing** – Maintain secure records of **transactions, refunds, and outstanding payments**.  
🔹 **Service Offerings** – Manage **onboard amenities** like meals, Wi-Fi, and in-flight entertainment.  

---

## **Database Structure & Tables**  

The system is built on an **SQL Server database**, with multiple tables ensuring **structured data storage**:  

| **Table Name**     | **Purpose** |  
|--------------------|------------|  
| **Airport**        | Stores airport details (ID, name, location, type) |  
| **Passenger**      | Manages passenger details (ID, name, contact info) |  
| **Flight_Details** | Logs flight schedules, aircraft type, and destinations |  
| **Service_Offering** | Tracks services like food, Wi-Fi, entertainment |  
| **Seat_Details**   | Manages seat allocation by travel class |  
| **Flight_Cost**    | Stores ticket pricing data |  
| **Reservation**    | Handles passenger flight bookings |  
| **Travel_Class**   | Defines seating classes (Economy, Business, First Class) |  
| **Calendar**       | Tracks flight schedules and availability |  
| **Payment_Status** | Manages transaction records and payment confirmations |  

---

## **Technology Stack**  

🖥 **Operating System:** Windows  
💾 **Database:** SQL Server  
📑 **Applications:** MS Word, MS PowerPoint  

---

## **Business Rules & Constraints**  

🔸 **Airport & Flights:** Each airport can have **multiple flights** originating from it.  
🔸 **Seat Assignments:** A seat is **assigned to only one passenger per reservation**.  
🔸 **Payment Verification:** Payments must be **confirmed before a ticket is validated**.  
🔸 **Flight Services:** Certain **travel classes offer exclusive services** (e.g., First Class lounge access).  
🔸 **Data Redundancy Prevention:** The database ensures **efficient storage** to reduce duplicate records.  

---

## **Database Queries & Reports**  

Below are some key SQL queries used to retrieve and analyze data:  

📌 **1. List all flights available in a specific country:**  
```sql
SELECT * FROM Airport WHERE Airport_Country = 'United States';
```

📌 **2. Retrieve payment status for a specific passenger:**  
```sql
SELECT RS.Reservation_ID, PS.Payment_Status_YN, PS.Payment_Due_Date, PS.Payment_Amount
FROM Reservation RS
JOIN Payment_Status PS ON RS.Reservation_ID = PS.Reservation_ID
JOIN Passenger P ON RS.Passenger_ID = P.Passenger_ID
WHERE P.P_FirstName = 'Alice' AND P.P_LastName = 'Johnson';
```

📌 **3. Display total passengers on an Airbus A380 flight:**  
```sql
SELECT COUNT(*) AS TotalPassengers
FROM Flight_Details
WHERE Airplane_Type = 'Airbus A380';
```

📌 **4. Retrieve the count of available seats by travel class:**  
```sql
SELECT TC.Travel_Class_Name, TC.Travel_Class_Capacity - COUNT(SD.Seat_ID) AS AvailableSeats
FROM Travel_Class TC
LEFT JOIN Seat_Details SD ON TC.Travel_Class_ID = SD.Travel_Class_ID
GROUP BY TC.Travel_Class_Name, TC.Travel_Class_Capacity;
```

📌 **5. Retrieve flight details along with departure and arrival airport names:**  
```sql
SELECT F.Flight_ID, F.Departure_Date_Time, F.Arrival_Date_Time, F.Airplane_Type, 
       A1.Airport_Name AS Departure_Airport, A2.Airport_Name AS Destination_Airport
FROM Flight_Details F
JOIN Airport A1 ON F.Airport_ID = A1.Airport_ID
JOIN Airport A2 ON F.Destination_Airport_ID = A2.Airport_ID;
```

📌 **6. List all services offered in First Class:**  
```sql
SELECT FS.Service_Name
FROM Service_Offering SO
JOIN Flight_Service FS ON SO.Service_ID = FS.Service_ID
WHERE SO.Travel_Class_ID = 1;
```

---

## **Conclusion**  

The **Flight Booking System** is a robust, scalable database solution designed to **enhance airline operations** by offering:  

✈ **Real-time booking updates**  
✈ **Seamless payment processing**  
✈ **Efficient seat allocation**  
✈ **Customizable passenger services**  
✈ **Comprehensive flight data reporting**  

This system ensures **data security, accuracy, and passenger convenience**, making air travel **more efficient and user-friendly**.  

---

## **Getting Started**  

### **1️⃣ Clone the Repository**  
```sh
git clone https://github.com/your-repo-name.git
cd your-repo-name
```

### **2️⃣ Set Up the Database**  
- Install **SQL Server** and **import the provided SQL schema**.  
- Run the **CREATE TABLE** scripts to initialize the database.  
- Populate the database with **INSERT statements** for sample data.  

### **3️⃣ Run Queries & Reports**  
- Execute the **predefined SQL queries** to test functionality.  
- Modify queries for **custom reports and analysis**.  

### **4️⃣ Extend & Customize**  
- **Enhance UI** with a web-based front end.  
- **Integrate APIs** for real-time flight tracking.  
- **Improve analytics** with **Power BI visualizations**.  

---

### **Future Enhancements**  

🚀 **AI-Based Pricing Predictions** – Use **machine learning** to optimize ticket prices.  
📊 **Dynamic Seat Allocation** – Implement **real-time seat assignment algorithms**.  
🌍 **Multi-Language Support** – Improve **global accessibility** for passengers.  
💳 **Secure Digital Wallet Integration** – Add **cryptocurrency & digital payment options**.  

---
