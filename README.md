# Pharmacy Product Data Management System (Updating System V1.4)

## Overview

This project is a comprehensive data management system designed for pharmacy product inventory, pricing, and application data. It provides a C++ console application for managing and synchronizing product data across multiple sheets (Stock, Price, App), with robust support for CSV, HTML, and Excel file formats. The system also includes Python utilities for file conversion and advanced data processing.

---

## Table of Contents

- [Features](#features)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Usage Guide](#usage-guide)
- [C++ Application Details](#c-application-details)
- [Python Utilities](#python-utilities)
- [Logging](#logging)
- [Build & Configuration](#build--configuration)
- [Contributing](#contributing)
- [License](#license)

---

## Features

- **Multi-format Support:** Handles CSV, HTML, and Excel (XLSX/XLS) files.
- **Automated Conversion:** Converts HTML/Excel sheets to CSV using Python.
- **Data Synchronization:** Synchronizes App Sheet with Stock and Price Sheets (VLOOKUP-like logic).
- **Advanced Operations:** Update, add, sort, export, and clean data with a variety of built-in operations.
- **Logging:** All changes and operations are logged with timestamps.
- **Cross-language Integration:** Seamless C++ and Python interoperability for data processing.

---

## Project Structure

```
Updating System V1.4 (Github)/
│
├── main.cpp                # Main C++ application (entry point, user interface)
├── operations.cpp/.h       # Core data operations (search, update, sync, etc.)
├── file_handler.cpp/.h     # CSV file reading/writing utilities
├── logger.cpp/.h           # Logging utility (writes to log.txt)
│
├── html_to_csv_converter.py # Python: Converts HTML/Excel to CSV
├── sort_csv_by_column.py    # Python: Sorts CSV by column, cleans SKU data
│
├── log.txt                 # Log file (auto-generated, tracks all changes)
│
├── bin/                    # Compiled executables (Debug/Release)
├── obj/                    # Object files (build artifacts)
├── .vscode/                # VSCode configuration (optional)
├── Updating System V1.3.cbp # Code::Blocks project file
├── Updating System V1.3.depend/.layout # Build and layout files
```

---

## Getting Started

### Prerequisites

- **C++ Compiler:** GCC (MinGW recommended for Windows)
- **Python 3.x:** Required for file conversion and sorting scripts
- **Python Packages:** `pandas`, `openpyxl`  
  Install with:
  ```
  pip install pandas openpyxl
  ```

### Build Instructions

1. **Using Code::Blocks:**  
   Open `Updating System V1.3.cbp` and build the project (Debug/Release).

2. **Using Command Line (MinGW):**
   ```sh
   g++ -std=gnu++17 -Wall -o bin/Debug/UpdatingSystem main.cpp operations.cpp file_handler.cpp logger.cpp
   ```

3. **Ensure Python is in your PATH** and required packages are installed.

---

## Usage Guide

### 1. **Launching the Application**

Run the executable from `bin/Debug/` or your build output directory:
```sh
./Updating\ System\ V1.exe
```

### 2. **File Input**

- The program will prompt for paths to the Stock, Price, and App sheets.
- Supports `.csv`, `.html`, `.htm`, `.xlsx`, `.xls` files.
- If a non-CSV file is provided, it will attempt conversion using `html_to_csv_converter.py`.

### 3. **Main Menu Options**

The application provides a menu-driven interface with the following options:

1. **Search for a product by code** (in Stock, Price, or App sheet)
2. **Update stock** in Stock Sheet
3. **Update price** in Price Sheet
4. **Add a new product** (to any sheet)
5. **Synchronize and update App Sheet** (VLOOKUP from Stock/Price)
6. **Sort App Sheet by SKU** & remove rows with multiple numbers in SKU
7. **Export App Sheet** (to a new file)
8. **Save All Sheets and Exit**
9. **Delete first 10 rows** from Price Sheet
10. **Unmerge columns I & J** in Price Sheet
11. **Move P column (الكود) to H column** in Price Sheet
12. **Delete repeated (السعر) column** from Price Sheet
13. **Delete first 6 columns** from Price Sheet
14. **Set home nursing services stock to 9000000** in App Sheet
15. **Convert all nan values to 0** in App Sheet

---

## C++ Application Details

### **main.cpp**
- Handles user interaction, menu, and file input/output.
- Calls Python scripts for file conversion and sorting as needed.
- Manages the main loop and dispatches operations.

### **operations.cpp / operations.h**
- Implements all core data operations:
  - Product search, stock/price update, product addition
  - App Sheet synchronization (VLOOKUP logic)
  - Data cleaning (remove rows, unmerge columns, etc.)
  - Exporting and saving sheets

### **file_handler.cpp / file_handler.h**
- Provides CSV reading and writing utilities.
- Handles parsing and serializing 2D data.

### **logger.cpp / logger.h**
- Logs all changes and operations to `log.txt` with timestamps.

---

## Python Utilities

### **html_to_csv_converter.py**
- Converts HTML tables and Excel files to CSV.
- Can be run standalone or called by the C++ app.
- Usage:
  ```sh
  python html_to_csv_converter.py --single-file input.html output.csv
  ```

### **sort_csv_by_column.py**
- Sorts a CSV file numerically by a specified column (e.g., SKU).
- Removes rows with multiple numbers in SKU and those with numbers longer than 6 digits.
- Usage:
  ```sh
  python sort_csv_by_column.py input.csv output.csv sku
  ```

---

## Logging

- All significant operations (updates, synchronizations, sorts, etc.) are logged in `log.txt`.
- Each entry includes a timestamp and a description of the change.

---

## Build & Configuration

- **Code::Blocks:** Project file provided (`.cbp`).
- **VSCode:** Includes `.vscode/` settings for IntelliSense and file associations.
- **Compiler:** Configured for GCC, C++17 standard.
- **Dependencies:** Only standard C++ libraries and Python packages (`pandas`, `openpyxl`).

---

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for terms.
