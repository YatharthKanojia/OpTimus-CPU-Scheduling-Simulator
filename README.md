# OpTimus – CPU Scheduling Simulator

**OpTimus** is a web-based CPU Scheduling Simulator built with **Flask**, **Socket.IO**, and **Selenium** that helps users visualize how various CPU scheduling algorithms work in real-time. This educational tool simulates how processes are managed by the CPU using algorithms like **FCFS**, **SJF**, **Priority Scheduling**, and **Round Robin**. It opens a new Chrome tab for each simulated process to give a visual cue of process execution.

It is useful for students, educators, and developers who want to understand or demonstrate process scheduling concepts in operating systems.

---

## 🚀 Features

- Add custom processes with:
  - **Process ID**
  - **Arrival Time**
  - **Burst Time**
  - **Priority**

- Supports major CPU scheduling algorithms:
  - **First-Come-First-Serve (FCFS)**
  - **Shortest Job First (SJF)**
  - **Round Robin** (with configurable time quantum)
  - **Priority Scheduling**

- Real-time simulation using Chrome tabs to represent process execution

- Real-time logging and status updates using **Flask-SocketIO**

- Results page showing:
  - **Waiting Time**
  - **Turnaround Time**
  - **Start and Completion Time**
  - **CPU Utilization**

- Reset and clear functionality for clean re-execution

---

## 📦 Prerequisites

- Python 3.8+
- Google Chrome Browser
- Google ChromeDriver (must be compatible with your Chrome version)
- Python Packages:
  ```bash
  pip install flask flask-socketio selenium


## 📁 Explanation of Each File

### `main.py`
- The Flask application entry point.
- Hosts the main endpoints:
  - `/add_process` – Add a new process
  - `/start` – Start the scheduling
  - `/results` – Fetch result data
  - `/reset` – Reset the scheduler
- Serves `index.html` and `result.html`
- Uses SocketIO to emit real-time logs and events to the front-end.

### `process.py`
- Defines the `DummyProcess` class.
- Each process is simulated using:
  - A background thread
  - A Selenium-controlled Chrome tab (for visual representation)
- Includes logic to:
  - Start
  - Pause
  - Resume
  - Terminate Chrome tabs
- This simulates the "execution" of a process in an OS environment.

### `scheduler.py`
- Contains the core logic for CPU scheduling.
- Defines the `Scheduler` class with methods for:
  - FCFS
  - SJF
  - Priority Scheduling
  - Round Robin (with time quantum and preemption)
- Executes processes in the correct order and logs timing info.

### `index.html`
- Front-end UI to interact with the scheduler.
- Built with Bootstrap 5 and vanilla JavaScript.
- Features:
  - Add process form
  - Algorithm selector
  - Time quantum input (conditionally shown)
  - Process queue viewer
  - Start/reset button
  - Live logs via Socket.IO

### `result.html`
- Displays scheduling results in a tabular format.
- Pulls data from the `/results` API.
- Presents:
  - Process execution metrics
  - A basic structure for adding Gantt Chart visuals if needed
