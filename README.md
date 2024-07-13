# SJF-Frontend
Frontend code for SJF (Preemptive/Non-Preemptive)
# Install dependencies
-> Run `npm i` to install dependencies.
# Start Project
-> Use `npm start` to start the server.
# To change project PORT for connection
-> To change or port, open `Runtime.ts`.
# Connect Frontend and Backend
-> Ensure the port in `main.go` for the backend matches the port specified in `Runtime.ts` in the frontend repository.
# Demo Video
-> [Video](https://drive.google.com/file/d/1Z0yilZV_bkcaKZvwv9taAu_zTguetHS8/view?usp=drive_link)
# SJF Backend Repo Link
-> [Backend](https://github.com/MISHRA7752/SJF-backend)

# Summary 
This project involves running jobs in two different modes: Preemptive Shortest Job First (SJF) and Non-Preemptive SJF. Below are the detailed descriptions and functionalities of each mode, along with the toggling mechanism and context switching behavior.

# Job Scheduling System

This project involves running jobs in two different modes: Preemptive Shortest Job First (SJF) and Non-Preemptive SJF. Below are the detailed descriptions and functionalities of each mode, along with the toggling mechanism and context switching behavior.

## Modes of Operation

### 1. Preemptive SJF

- **Description:** In Preemptive SJF mode, the system can interrupt a currently running job if a new job with a shorter execution time arrives.
- **Time Quantum:** When you turn on Preemptive mode, a popup will ask for a time quantum value. This time quantum determines the maximum time a job can run before a context switch occurs.
- **Context Switching:** If a large job is running and a smaller job arrives, the system will perform a context switch after the specified time quantum to check for and possibly run the smaller job.

### 2. Non-Preemptive SJF

- **Description:** In Non-Preemptive SJF mode, once a job starts running, it runs to completion without interruption. New jobs are sorted in order of their execution time and executed sequentially.
- **Context Switching:** The job that starts running will continue without switching until it completes. Subsequent jobs are arranged in sorted order and executed based on their arrival time and execution time.

## Toggling Between Modes

- **Condition:** You can only toggle between Preemptive and Non-Preemptive modes when no jobs are currently running.
- **Preemptive to Non-Preemptive:** When you switch from Preemptive to Non-Preemptive mode, the currently running job will continue uninterrupted. New jobs will be arranged in sorted order and executed sequentially.

## Job Execution and WebSocket Communication

- **Context Switching and Completion:** Whenever a job completes or a context switch occurs, a message is broadcasted via WebSocket. This allows the system to fetch the latest jobs array and update with the most recent data.
- **Job Addition:** When adding a new job, the system checks the current mode and handles the job accordingly:
  - In Preemptive mode, it checks if a context switch is necessary.
  - In Non-Preemptive mode, it adds the job to the sorted list of pending jobs.

This job scheduling system efficiently manages job execution by allowing dynamic switching between Preemptive and Non-Preemptive modes. It ensures optimal job handling based on the selected mode and keeps the system updated in real-time through WebSocket communication.


