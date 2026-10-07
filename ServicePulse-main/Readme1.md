# 🚀 ServicePulse — Service Monitoring System

ServicePulse is a lightweight Python-based **service monitoring and reporting application** designed to monitor the availability and performance of web services.

The application provides a graphical dashboard where users can add services, check their availability, monitor response time, view uptime statistics, generate response-time charts, and create HTML monitoring reports.

---

## 📌 Features

### 🖥️ Frontend / GUI

- Login interface
- Service Monitoring Dashboard
- Total Services statistics
- UP Services count
- DOWN Services count
- Overall uptime percentage
- Average response time
- Service table using Tkinter Treeview
- Color-coded service status
- Search services by name or URL
- Add new services
- URL validation
- Check all services manually
- Automatic dashboard refresh
- Detailed service statistics
- Response-time graphs
- HTML report generation
- Error and warning popups
- Responsive GUI during network monitoring using background threads

---

### 🌐 Service Monitoring

ServicePulse checks registered services and determines their availability.

For each service, the application can collect:

- Service status
- HTTP status code
- Response time
- Monitoring timestamp

The application categorizes services as:

- **UP** — HTTP response indicates that the service is responding
- **DOWN** — HTTP request fails or the service returns an unsuccessful response

---

### 📊 Analytics

The application calculates useful monitoring statistics such as:

- Total number of checks
- Successful checks
- Failed checks
- Uptime percentage
- Average response time
- Minimum response time
- Maximum response time

### Uptime Formula

```text
Uptime = (Successful Checks / Total Checks) × 100
```

Example:

```text
Successful Checks = 98
Total Checks = 100

Uptime = (98 / 100) × 100
       = 98%
```

---

### 📈 Response-Time Visualization

ServicePulse uses **Matplotlib** to generate response-time graphs.

The graph helps visualize how the response time of a service changes across monitoring checks.

The generated chart can be displayed from the dashboard.

---

### 📄 HTML Reports

ServicePulse can generate an HTML monitoring report containing service information and monitoring statistics.

The generated report can be opened directly in the system's default web browser.

---

### 🔄 Automatic Monitoring

The project also contains automation/scheduling functionality for periodic monitoring of services.

This allows monitoring tasks to be performed automatically instead of requiring the user to manually check every service.

---

# 🏗️ Project Architecture

```text
ServicePulse/
│
├── main.py
│
├── gui/
│   ├── login.py
│   ├── dashboard.py
│   └── service_form.py
│
├── database/
│   ├── db.py
│   └── servicepulse.db
│
├── monitoring/
│   └── monitor.py
│
├── analytics/
│   └── charts.py
│
├── reports/
│   └── html_report.py
│
├── automation/
│   └── scheduler.py
│
├── reports/
│   └── index.html
│
└── README.md
```

---

# 🧩 Module Description

## 1. `main.py`

The main entry point of the application.

It initializes the Tkinter application and starts the ServicePulse dashboard.

---

## 2. `gui/`

Contains the graphical user interface.

### `login.py`

Provides the login interface.

Features include:

- Username input
- Password input
- Login validation
- Exit functionality

### `dashboard.py`

The main GUI of ServicePulse.

It provides:

- Dashboard
- Service table
- Search
- Add Service
- Check All
- Statistics
- Charts
- Report generation
- Status updates

### `service_form.py`

Provides an additional form for entering service information.

---

## 3. `database/`

Handles database operations.

The project uses **SQLite** for storing service and monitoring information.

Typical database operations include:

- Adding services
- Retrieving services
- Searching services
- Saving monitoring results
- Retrieving monitoring history

---

## 4. `monitoring/`

Contains the service monitoring logic.

The monitoring module checks web services and collects information such as:

```text
URL
HTTP Status Code
Response Time
Status
```

---

## 5. `analytics/`

Contains data analysis and visualization functionality.

The chart module uses **Matplotlib** to create response-time graphs from monitoring history.

---

## 6. `reports/`

Responsible for generating HTML monitoring reports.

The generated report presents monitoring information in a readable web-based format.

---

## 7. `automation/`

Contains scheduling functionality for automatically performing monitoring tasks at predefined intervals.

---

# 🛠️ Technologies Used

| Technology  | Purpose                   |
| ----------- | ------------------------- |
| Python      | Main programming language |
| Tkinter     | Desktop GUI               |
| Tkinter ttk | Themed GUI widgets        |
| SQLite      | Database                  |
| Matplotlib  | Data visualization        |
| Threading   | Background monitoring     |
| HTML        | Monitoring reports        |
| Webbrowser  | Opening generated reports |
| `datetime`  | Timestamps                |
| `os`        | File/path handling        |

---

# 📦 Python Libraries

The project primarily uses Python's standard libraries along with Matplotlib.

### Standard Libraries

```python
tkinter
sqlite3
threading
webbrowser
datetime
os
sys
```

### External Library

```text
matplotlib
```

---

# 💻 Requirements

Recommended environment:

- Python 3.10+
- Windows / Linux / macOS
- Internet connection for monitoring external websites

---

# ⚙️ Installation

## 1. Clone or download the project

```bash
git clone <repository-url>
cd ServicePulse
```

If you downloaded the ZIP file, extract it and open a terminal inside the project directory.

---

## 2. Check Python Installation

Run:

```bash
python --version
```

or:

```bash
python3 --version
```

Python 3.10 or later is recommended.

---

## 3. Install Required Package

Install Matplotlib:

```bash
pip install matplotlib
```

If your system uses `python3`:

```bash
pip3 install matplotlib
```

---

# ▶️ Running the Application

From the project root directory, run:

```bash
python main.py
```

The ServicePulse dashboard should open.

---

# 🔐 Login

If the login interface is used, the current development credentials are:

```text
Username: admin
Password: admin
```

> **Note:** The current login implementation uses development credentials rather than database-backed authentication.

---

# 🖥️ Using the Dashboard

After opening ServicePulse, the dashboard provides several operations.

## Add a Service

1. Click **Add Service**.
2. Enter the service name.
3. Enter the service URL.
4. Validate the URL.
5. Save the service.

Example:

```text
Service Name:
Google

URL:
https://www.google.com
```

---

## Search for a Service

Enter a service name or URL in the search box.

Example:

```text
Google
```

or:

```text
https://www.google.com
```

Then click **Search**.

---

## Check All Services

Click:

```text
Check All Now
```

The application checks all registered services.

The monitoring process runs in a background thread so that the GUI remains responsive.

---

## View Statistics

Select a service and click:

```text
View Chart & Stats
```

The application displays information such as:

```text
Uptime
Total Checks
Average Response Time
Minimum Response Time
Maximum Response Time
```

---

## View Response-Time Graph

The application uses Matplotlib to generate a graph showing response-time history.

This allows users to identify performance changes over time.

---

## Generate Report

Click:

```text
Generate Report
```

The application generates an HTML report containing monitoring information.

The report can then be opened in a web browser.

---

# 🔄 Monitoring Workflow

The basic monitoring workflow is:

```text
User
 │
 ▼
ServicePulse GUI
 │
 ▼
Select / Add Service
 │
 ▼
Database
 │
 ▼
Monitoring Module
 │
 ▼
HTTP Request
 │
 ├── Response Status
 │
 └── Response Time
 │
 ▼
Monitoring Result
 │
 ▼
SQLite Database
 │
 ├── Statistics
 │
 ├── Charts
 │
 └── HTML Report
```

---

# 🧵 Background Monitoring

ServicePulse uses Python's `threading` module for monitoring operations.

Without threading:

```text
GUI
 │
 ▼
Check Website
 │
 ▼
Wait for Response
 │
 ▼
GUI freezes
```

With threading:

```text
                ┌──► GUI remains responsive
                │
Main Program ───┤
                │
                └──► Background Thread
                           │
                           ▼
                     Check Services
```

This improves the user experience during network operations.

---

# 🔄 Automatic GUI Refresh

The dashboard uses Tkinter's:

```python
root.after()
```

method to schedule periodic updates.

For example:

```python
root.after(5000, auto_refresh)
```

means the refresh operation is scheduled after 5000 milliseconds.

```text
5000 milliseconds = 5 seconds
```

Unlike `time.sleep()`, `after()` does not block the Tkinter event loop.

---

# 📊 Database

ServicePulse uses SQLite because it is:

- Lightweight
- Serverless
- File-based
- Easy to integrate with Python
- Suitable for a small monitoring application

The database stores information related to:

- Services
- Monitoring logs
- Users / authentication data where applicable

---

# 📐 Uptime Calculation

Uptime is calculated using:

```text
Uptime (%) =
(UP Checks / Total Checks) × 100
```

Example:

```text
Total Checks = 500
UP Checks = 493

Uptime = (493 / 500) × 100
       = 98.6%
```

---

# 🎨 GUI Components

The project uses several Tkinter components.

| Component    | Purpose                        |
| ------------ | ------------------------------ |
| `Tk()`       | Main application window        |
| `Toplevel()` | Secondary window               |
| `Frame`      | Organize widgets               |
| `Label`      | Display text                   |
| `Entry`      | Accept user input              |
| `Button`     | Trigger actions                |
| `Treeview`   | Display service table          |
| `Scrollbar`  | Scroll through service data    |
| `messagebox` | Display alerts                 |
| `PhotoImage` | Display generated chart images |

---

# 📁 Data Flow

```text
                    ┌─────────────┐
                    │   Tkinter   │
                    │     GUI     │
                    └──────┬──────┘
                           │
             ┌─────────────┼─────────────┐
             │             │             │
             ▼             ▼             ▼
        Database      Monitoring      Analytics
             │             │             │
             │             ▼             ▼
             │        HTTP Check     Matplotlib
             │             │             │
             └─────────────┼─────────────┘
                           │
                           ▼
                    HTML Reporting
```

---

# 🔒 Error Handling

The application uses exception handling to prevent unexpected errors from crashing the GUI.

Examples include:

- Invalid URLs
- Database errors
- Monitoring failures
- Missing service selection
- Chart generation errors
- Report generation errors
- Invalid login credentials

Errors and warnings are displayed using Tkinter message boxes.

---

# 🎯 Project Objectives

The main objectives of ServicePulse are:

1. Monitor web service availability.
2. Measure service response time.
3. Store monitoring history.
4. Calculate uptime statistics.
5. Provide a user-friendly dashboard.
6. Visualize response-time data.
7. Generate monitoring reports.
8. Support automated monitoring.
9. Keep the GUI responsive during network operations.

---

# 🌟 Key Highlights

- Lightweight desktop monitoring system
- Modular Python architecture
- Tkinter-based GUI
- SQLite database
- Real-time service checking
- Response-time monitoring
- Uptime calculation
- Data visualization
- HTML report generation
- Background monitoring using threads
- Automatic dashboard refresh

---

# 🔮 Future Scope

Possible improvements include:

- Database-backed user authentication
- Password hashing and secure authentication
- Role-based access control
- Email/SMS alerts
- Cloud database integration
- Cloud deployment
- Advanced predictive analytics
- Machine-learning-based failure prediction
- More detailed monitoring metrics
- Historical dashboard filtering
- Export reports as PDF/CSV
- REST API integration
- Multi-user support
- Improved monitoring scheduler
- Docker deployment

---

# ⚠️ Current Limitations

- The current login implementation uses development credentials.
- The application primarily focuses on HTTP-based service monitoring.
- The project uses a local SQLite database.
- Some GUI components are implemented as alternative/legacy forms and may require synchronization with the current database function signatures.
- Monitoring external services requires an active network connection.

---

# 👥 Project Structure by Responsibility

The project can be divided into the following functional areas:

### GUI / Frontend

Responsible for:

- Login
- Dashboard
- Service management
- Search
- Statistics
- Charts
- Reports

### Database

Responsible for:

- Data storage
- Service records
- Monitoring logs
- Database queries

### Monitoring

Responsible for:

- HTTP requests
- Availability checking
- Response-time measurement
- Status determination

### Analytics

Responsible for:

- Statistics
- Response-time analysis
- Graph generation

### Reporting

Responsible for:

- HTML report generation
- Report presentation

### Automation

Responsible for:

- Scheduled monitoring
- Periodic checks

---

# 🧪 Example Monitoring Result

```text
Service: Google
URL: https://www.google.com

Status: UP
HTTP Status Code: 200
Response Time: 120 ms

Uptime: 99.8%
```

Another example:

```text
Service: Example Service
URL: https://example.com

Status: DOWN
HTTP Status Code: 500
Response Time: 350 ms
```

---

# 📚 Learning Outcomes

Through this project, the following concepts are demonstrated:

- Python programming
- Object-oriented programming
- GUI development
- Event-driven programming
- SQLite database management
- SQL queries
- HTTP service monitoring
- Multithreading
- Exception handling
- Data analysis
- Data visualization
- HTML report generation
- Modular software architecture
- File and path handling

---

# 👨‍💻 Project

**Project Name:** ServicePulse
**Type:** Service Monitoring System
**Language:** Python
**GUI:** Tkinter
**Database:** SQLite
**Visualization:** Matplotlib
**Report Format:** HTML

---

## 📜 License

This project was developed for educational and academic purposes.

---

## ⭐ Conclusion

ServicePulse provides a complete lightweight service-monitoring solution combining a Python desktop GUI, SQLite database, HTTP monitoring, analytics, visualization, and HTML reporting.

The system allows users to monitor service availability and performance through a centralized dashboard while maintaining historical monitoring information for analysis and reporting.
