
# Billing Software

A Java-based Billing Software designed for retail stores and small businesses to streamline billing and inventory management. Built using **Java Swing**, **MySQL**, and **iText**, this application provides a user-friendly GUI for managing products, generating bills, and creating PDF invoices.

## 🔧 Features

* Add, update, delete, and view product details.  
* Generate and manage bills.  
* Automatic total calculation.  
* PDF invoice generation using iText.  
* Secure transaction record storage with MySQL.  
* Interactive and responsive GUI using Java Swing.  

## 🛠️ Technologies Used

* **Java Swing** – GUI development  
* **MySQL** – Database management  
* **JDBC** – Java Database Connectivity  
* **iText** – PDF generation  

## 📦 Libraries Used

### 1. **AbsoluteLayout.jar**
Used for absolute positioning of Swing components. Typically utilized with NetBeans GUI Builder for visually designing user interfaces.

### 2. **PostgreSQL JDBC Driver (postgresql-42.5.4.jar)**
Allows the application to connect and interact with a PostgreSQL database via JDBC.

### 3. **MySQL JDBC Driver (mysql-connector-j-9.2.0.jar)**
Enables Java applications to connect to and interact with MySQL databases.

### 4. **Java EE 6 Endorsed API Libraries**
- `javax.annotation.jar`: Provides standard Java annotations like `@PostConstruct`, `@PreDestroy`, etc.
- `jaxb-api-osgi.jar`: Used for Java-XML data binding via JAXB.
- `webservices-api-osgi.jar`: Provides API support for building SOAP-based web services.

### 5. **rs2xml.jar**
Facilitates the easy population of `JTable` components with data from a JDBC `ResultSet`.

### 6. **itextpdf-5.1.0.jar**
Library used to generate and manipulate PDF documents. Useful for exporting reports and documents from the application.

## ☕ JDK Used

- **Java Development Kit (JDK) 23**  
  This project is compiled and run using JDK 23.

---

## 📌 Notes
- Ensure all `.jar` files are included in your project's build path.
- Use the appropriate JDBC driver depending on whether you're connecting to MySQL or PostgreSQL.
- If using NetBeans, drag-and-drop UI components with AbsoluteLayout for easier UI design.


## 📸 Screenshots
**Home**  
![image](https://github.com/user-attachments/assets/9556996c-c894-44f8-9c87-ddc9517540d9)

**Add Product**  
![Add Product](https://github.com/user-attachments/assets/95c3e8cc-71c4-44bd-838c-b087af3dcf6a)

**Product Details**  
![Product Details](https://github.com/user-attachments/assets/49624ff5-4a80-4039-8da9-aca4ed13ffa7)

**Product Billing**  
![Product Billing](https://github.com/user-attachments/assets/79b55045-e9cc-4b7e-8246-d71f68281899)

**Invoice stored by customer name and date**  
![image](https://github.com/user-attachments/assets/16ab631c-3f73-4733-beec-d32379762e4d)


## 📦 Installation & Setup

### 1. Clone the repository

```bash
git clone https://github.com/tamilamudan/Billing-Software.git
cd Billing-Software
```

### 2. Setup the MySQL Database

Log in to your MySQL server using terminal or MySQL Workbench:

```bash
mysql -u root -p
```

Run the following SQL commands to create the database and tables:

```sql
CREATE DATABASE billingsoftware;
USE billingsoftware;

CREATE TABLE product (
    pID INT PRIMARY KEY,
    pName VARCHAR(100),
    rate INT,
    description VARCHAR(200),
    activate VARCHAR(10)
);

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL
);
```

### 3. Configure Database Connection

Open `src/project/ConnectionProvider.java` and update the credentials as needed:

```java
package project;

import java.sql.Connection;
import java.sql.DriverManager;

public class ConnectionProvider {
    public static Connection getCon() {
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/billingsoftware",
                "root",            // <-- your MySQL username here
                "your_password"    // <-- your MySQL password here
            );
            return con;
        } catch (Exception e) {
            e.printStackTrace();
            return null;
        }
    }
}
```

### 4. Build and Run the Application

#### Using the Command Line

Compile and run from the project root folder:

```bash
javac -d bin src/project/ConnectionProvider.java src/login.java
java -cp bin login
```

#### Using NetBeans IDE

1. Open NetBeans, select **File > Open Project**, and open the cloned project folder.  
2. Make sure your MySQL server is running.  
3. Update your database credentials in `ConnectionProvider.java` as shown above.  
4. Right-click on `login.java` in the project explorer and select **Run File**.  

## 🚀 Usage

* Use the GUI to add, update, and delete products.  
* Generate bills by selecting products and quantities.  
* Save and view PDF invoices named by customer and date.  
* Manage user accounts through the `users` table for authentication (if implemented).  

## 📝 Notes

* Ensure your MySQL server is running before launching the application.  
* The PDF invoices are stored locally on your system for each transaction.  
