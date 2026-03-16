# Call Center Queue System

## Description

The **Call Center Queue System** is a console-based C++ application that simulates how a real call center manages incoming customer calls using a **queue data structure**. Calls are received and added to the back of the queue, and agents handle them in the order they arrived — following the classic **FIFO (First In, First Out)** principle.

The queue is implemented using a fixed-size array, making it lightweight and dependency-free. This project is a practical demonstration of how queues are applied in real-world systems such as customer support centers, ticketing systems, and task schedulers.

### Key concepts used

- **Queue (FIFO)** — the first call received is always the first to be handled, just like a real call center waiting line.
- **Array-based queue** — the queue is backed by a static array of size `MAX = 100`, with `front` and `rear` pointers tracking the active range.
- **Structs** — `Call` holds the data for a single call (ID, caller name, issue); `CallQueue` encapsulates all queue operations.
- **Enqueue / Dequeue** — new calls are added at the rear; agents pick calls from the front.
- **Boundary checks** — `isFull()` and `isEmpty()` guards prevent overflow and underflow.

### Features

- Receive incoming calls with caller name and issue description
- Auto-incremented call IDs for every new call
- Handle the next call in queue (FIFO order) with a full summary
- Display all currently waiting calls in the queue
- Overflow protection — rejects new calls if the queue is full

---

## Build and run

**Requirements:** any C++11-compatible compiler (g++, clang++, etc.)

```bash
# Compile
g++ -std=c++11 -o call_center call_center_queue.cpp

# Run
./call_center
```

---

## Example session

```
=== Call Center Menu ===
1. Receive Call
2. Handle Next Call
3. Display Queue
4. Exit
Enter your choice: 1
Enter caller name: Alice
Enter issue description: Internet not working
Call added to queue.

Enter your choice: 1
Enter caller name: Bob
Enter issue description: Billing query
Call added to queue.

Enter your choice: 3

Current Calls in Queue:
----------------------------
ID: 1  |  Caller: Alice  |  Issue: Internet not working
ID: 2  |  Caller: Bob    |  Issue: Billing query
----------------------------

Enter your choice: 2

--- Handling Call ---
Call ID : 1
Caller  : Alice
Issue   : Internet not working
Call handled successfully!
```

---

## How the queue works

```
Receive calls → [ Call1 | Call2 | Call3 ]  ← rear
                   ↑
                 front (handled first)

After handling Call1 → [ Call2 | Call3 ]
                          ↑
                        front
```

The `front` pointer advances on each dequeue. When `front > rear`, the queue is considered empty.

---

## Project structure

```
.
└── call_center_queue.cpp   # Full source — single file, no dependencies
```

---

## Limitations & possible improvements

- The current implementation is a **linear array queue** — once `rear` reaches `MAX - 1`, no more calls can be added even if earlier slots were freed. This can be solved by implementing a **circular queue**.
- Call data is not persisted to a file; records are lost on exit.
- A priority queue variant could handle VIP or urgent calls first.

---

## License

MIT — feel free to use and adapt.
