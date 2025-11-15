# Pintos Project – Phase 1 & Phase 2

This repository contains my implementation of the Pintos Operating System assignments.  
It includes the complete solutions for:

- **Phase 1: Alarm Clock**
- **Phase 2: Priority Scheduler**

Both phases were implemented inside the Pintos kernel (`threads/` directory).

---

##  Phase 1: Alarm Clock 

### Goal
Implement `timer_sleep()` so that threads sleep **without busy-waiting**, using proper timer-interrupt-based synchronization.

### Key Features
- Non–busy-wait sleeping
- Uses ordered sleep list + timer interrupts
- Proper thread blocking and unblocking
- Handles zero and negative sleep values safely

### Tests Passed
All official Pintos alarm tests:

| Test | Result |
|------|--------|
| alarm-single | ✔ Passed |
| alarm-multiple | ✔ Passed |
| alarm-simultaneous | ✔ Passed |
| alarm-zero | ✔ Passed |
| alarm-negative | ✔ Passed |

_No busy-waiting or improper interrupt disabling was used._

---

## Phase 2: Priority Scheduler

### Goal
Implement priority-based scheduling with full priority donation support.

### Key Features
- Highest priority thread is always scheduled first
- Implements:
  - Priority preemption
  - Priority donation (single & nested)
  - Donation chains
  - Donation with locks, semaphores, and condition variables
- FIFO ordering for equal priorities
- Priority-aware blocking and waking

### Tests Passed

| Test | Result |
|------|--------|
| alarm-priority | ✔ Passed |
| priority-change | ✔ Passed |
| priority-preempt | ✔ Passed |
| priority-fifo | ✔ Passed |
| priority-sema | ✔ Passed |
| priority-condvar | ✔ Passed |
| priority-donate-one | ✔ Passed |
| priority-donate-multiple | ✔ Passed |
| priority-donate-multiple2 | ✔ Passed |
| priority-donate-nest | ✔ Passed |
| priority-donate-chain | ✔ Passed |
| priority-donate-sema | ✔ Passed |
| priority-donate-lower | ✔ Passed |
-------

##  Directory Structure (Relevant Files)
src/
└── threads/
├── thread.c
├── thread.h
├── synch.c
├── synch.h
├── timer.c
├── interrupt.c
└── tests/threads/

Main files modified:
- `thread.c`
- `synch.c`
- `timer.c`

---

##  Running Tests

Inside Pintos build directory:

```sh
cd threads/build
make

Run individual tests:

pintos run alarm-single
pintos run priority-donate-chain

Run all tests:
make check
