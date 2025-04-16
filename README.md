# Distributed Hash Table (DHT) Implementation in C++

This project implements a scalable, decentralized **Distributed Hash Table (DHT)** using C++. The system simulates a peer-to-peer network where nodes can dynamically join or leave, and data can be efficiently inserted, searched, and removed — all without relying on any centralized server.

The DHT uses consistent hashing to distribute keys across nodes and maintains optimized routing structures to ensure lookups complete in logarithmic time.

---

## 🚀 Features

- **Dynamic Node Management**  
  Supports adding and removing nodes without impacting the integrity of the overall system.

- **Efficient Key Lookups (O(log N))**  
  Each node maintains a compact routing table to locate the target node for any key quickly.

- **Consistent Hashing**  
  Keys and nodes are assigned positions in a circular identifier space using SHA-1 hashing, ensuring minimal data reshuffling on changes.

- **Data Operations**  
  Implemented core operations: `insert`, `find`, `remove`, and `join`.

- **Simulation Ready**  
  Includes a main simulation file with hardcoded inputs and test cases to demonstrate expected outputs.

---

## 🧱 Project Structure

.
├── Main.cpp            # Entry point of the program, simulates the DHT with sample operations
├── Node.cpp            # Contains the logic for each node in the network (insert, find, join, remove)
├── Node.h              # Header file for the Node class
├── FingerTable.cpp     # Implements routing logic for efficient key lookup (O(log N))
├── FingerTable.h       # Header file for FingerTable class
├── Helpers.cpp         # Utility functions for output formatting, printing routing paths, etc.
├── Helpers.h           # Header declarations for helper utilities
├── test_cases/         # (Optional) Folder for input/output sample test cases
└── README.md           # Project documentation


---

## 🔑 How It Works

- Each node is assigned a unique identifier by hashing its ID using SHA-1.
- Keys (data items) are also hashed and mapped to the closest node in the circular space.
- Nodes maintain routing tables pointing to other nodes at specific intervals, allowing them to jump closer to the target node rather than traversing sequentially.
- When a new node joins, it updates its routing table and triggers limited updates in the network to maintain consistency.

---

## 🧪 Example Operations

- `insert(key)` → Adds a key to the appropriate node
- `find(key)` → Returns the path taken and the node responsible for the key
- `remove(key)` → Deletes a key from the system
- `join(nodeID)` → Adds a new peer to the network and integrates it

---

## 🛠️ How to Compile & Run

Make sure you have `g++` installed. Then run:

```bash
g++ -o dht.exe Main.cpp Helpers.cpp Node.cpp FingerTable.cpp --std=c++11
./dht.exe
