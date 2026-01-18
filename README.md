# 🧠 LRU Cache System – Java

## 📌 Overview
This project implements an LRU (Least Recently Used) Cache in Java.  
The cache automatically evicts the least recently accessed item when the maximum capacity is reached, ensuring efficient memory usage.

Both 'get()' and 'put()' operations run in O(1) time complexity.

---

## 🚀 Features
- Constant time 'get(key)' and 'put(key, value)'
- Automatic eviction using LRU policy
- Efficient memory management
- Clean object-oriented design

---

## 🛠️ Technologies Used
- Java  
- HashMap  
- Doubly Linked List  
- Object-Oriented Programming  
- Data Structures & Algorithms  

---

## 🧩 Design Approach
To achieve constant-time operations:
- A HashMap stores key–node mappings for fast access
- A Doubly Linked List maintains the order of usage  
  - Most recently used items are near the head  
  - Least recently used items are near the tail  

This combination allows fast insertion, deletion, and lookup.

---

## 🧪 Operations

### get(int key)
- Returns the value if the key exists
- Moves the accessed element to the most recently used position
- Returns '-1' if the key is not present

### put(int key, int value)
- Inserts or updates a key-value pair
- Removes the least recently used item when capacity is exceeded

---
