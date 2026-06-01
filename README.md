<div align="center">

# 🎫 Queue Management System

![C++](https://img.shields.io/badge/C%2B%2B-17-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![STL](https://img.shields.io/badge/STL-queue%20%7C%20stack-0078D4?style=for-the-badge)
![OOP](https://img.shields.io/badge/Paradigm-OOP-2ea44f?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)

> A **C++ OOP Queue & Ticket Management System** — issue tickets, track waiting clients, estimate serve times, and visualize queue flow in real time.

</div>

---

## 📋 Table of Contents :

- [📖 About](#-about)
- [✨ Features](#-features)
- [🧱 Project Structure](#-project-structure)
- [🔍 Class Overview](#-class-overview)
- [🚀 Getting Started](#-getting-started)
- [🔧 How It Works](#-how-it-works)
- [🖥️ Sample Output](#️-sample-output)
- [💡 Use Cases](#-use-cases)
- [🛠️ Tech Stack](#️-tech-stack)
- [📄 CV Description](#-cv-description)
- [📃 License](#-license)

---

## 📖 About  :

**Queue Management System** is a C++ console application that simulates a real-world ticket-based queue system — the kind you see in banks, clinics, and government offices. Clients receive numbered tickets and are served in **FIFO** order, with live tracking of wait times and queue state.

Built as a focused OOP exercise to demonstrate **nested class design**, **STL container usage**, and **encapsulation** in a practical, real-world scenario.

---

## ✨ Features :

| Feature | Description |
|---|---|
| 🎟️ **Ticket Issuance** | Auto-numbered tickets with a custom prefix (e.g. `A1`, `B12`, `VIP3`) |
| ⏱️ **Live Timestamps** | Each ticket captures the exact date & time it was issued |
| 🧮 **Wait-Time Estimation** | Expected wait = `waiting clients × average serve time (mins)` |
| 👥 **Client Tracking** | Real-time count of waiting vs. served clients |
| ➡️ **RTL & LTR Visualization** | Print the queue flow left-to-right or right-to-left |
| 🗂️ **Full Ticket Slip** | Pretty-print individual ticket details (number, time, wait) |
| ✅ **FIFO Serving** | Serve next client with empty-queue guard |
| 📊 **Queue Report** | Summary of total, served, and waiting clients |

---

## 🧱 Project Structure :

```
Queue-Management-System/
│
├── clsQueueLine.h      # 🎯 Core queue engine + nested clsTicket class
├── clsDate.h           # 📅 Date/time utility (timestamp generation)
└── main.cpp            # 🚀 Entry point & demo driver
```

---

## 🔍 Class Overview :

```
clsQueueLine
│
├── 🔒 Private Members
│   ├── _TotalTickets         → cumulative ticket counter
│   ├── _AverageServeTime     → minutes to serve one client
│   ├── _Prefix               → ticket label prefix (A, B, VIP …)
│   │
│   └── class clsTicket       → nested ticket entity
│         ├── _Number             ticket number
│         ├── _Prefix             label prefix
│         ├── _TicketTime         issue timestamp
│         ├── _WaitingClients     clients ahead at issue time
│         ├── _AverageServeTime   inherited serve time
│         │
│         ├── FullNumber()        → "A3"
│         ├── ExpectedServeTime() → WaitingClients × AvgServeTime
│         └── Print()             → formatted ticket slip
│
└── 🔓 Public Interface
    ├── IssueTicket()           issue & enqueue a new ticket
    ├── ServeNextClient()       dequeue front client (FIFO)
    ├── WhoIsNext()             peek at front ticket number
    ├── WaitingClients()        current queue size
    ├── ServedClients()         total issued − waiting
    ├── PrintInfo()             queue summary report
    ├── PrintAllTickets()       print every ticket slip
    ├── PrintTicketsLineRTL()   visualize: A1 <-- A2 <-- A3
    └── PrintTicketsLineLTR()   visualize: A3 --> A2 --> A1
```

---

## 🚀 Getting Started :

### Prerequisites

- C++ 17 or later
- Any standard compiler: GCC, Clang, or MSVC

### Clone & Build

```bash
# 1️⃣ Clone the repository
git clone https://github.com/your-username/Queue-Management-System.git
cd Queue-Management-System

# 2️⃣ Compile
g++ -std=c++17 main.cpp -o QueueManagementSystem

# 3️⃣ Run
./QueueManagementSystem
```

---

## 🔧 How It Works :

```cpp
// 1️⃣ Create a queue — prefix "A", 5 minutes average serve time
clsQueueLine MyQueue("A", 5);

// 2️⃣ Issue tickets
MyQueue.IssueTicket();   // → A1  (0 waiting ahead)
MyQueue.IssueTicket();   // → A2  (1 waiting ahead → 5 min wait)
MyQueue.IssueTicket();   // → A3  (2 waiting ahead → 10 min wait)

// 3️⃣ Visualize the line
MyQueue.PrintTicketsLineRTL();
// Tickets:  A1 <-- A2 <-- A3

MyQueue.PrintTicketsLineLTR();
// Tickets:  A3 --> A2 --> A1

// 4️⃣ Serve next client
MyQueue.ServeNextClient();        // removes A1
cout << MyQueue.WhoIsNext();      // → A2

// 5️⃣ Full reports
MyQueue.PrintInfo();              // queue summary
MyQueue.PrintAllTickets();        // all remaining ticket slips
```

---

## 🖥️ Sample Output :

```
         _________________________

                Queue Info
         _________________________

             Prefix           = A
             Total Tickets    = 3
             Served Clients   = 1
             Waiting Clients  = 2
         _________________________


         Tickets:  A2 <-- A3


         ___________________________

                    A2

            2025-01-15 10:32:05
            Waiting Clients = 1
              Serve Time In
               5 Minutes.
         ___________________________

         ___________________________

                    A3

            2025-01-15 10:32:10
            Waiting Clients = 2
              Serve Time In
               10 Minutes.
         ___________________________
```

---

## 💡 Use Cases :

- 🏦 **Bank / Government Office** — teller and counter queues
- 🏥 **Clinic / Hospital** — patient appointment flow
- 🛒 **Retail** — checkout line management
- 🎓 **Academic** — demonstrates FIFO, OOP, STL `queue` & `stack`, nested classes, and encapsulation

---

## 🛠️ Tech Stack :

| Layer | Detail |
|---|---|
| **Language** | C++ 17 |
| **Data Structures** | `std::queue` (FIFO serving), `std::stack` (LTR reversal) |
| **Paradigm** | Object-Oriented Programming · Nested Classes · Encapsulation |
| **Utilities** | `clsDate` — custom date/time helper for ticket timestamps |
| **I/O** | Console (`std::cout`) |

---

## 🤝 Contributing :

Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to change.

---

<div align="center">
  Made with ❤️ and C++
</div>
