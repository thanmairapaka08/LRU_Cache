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

## 💻 Implementation

import java.util.HashMap;

class LRUCache {
    class Node {
        int key, value;
        Node prev, next;
        Node(int k, int v) {
            key = k;
            value = v;
        }
    }
    private int capacity;
    private HashMap<Integer, Node> map;
    private Node head, tail;
    public LRUCache(int capacity) {
        this.capacity = capacity;
        map = new HashMap<>();
        head = new Node(0, 0);
        tail = new Node(0, 0);
        head.next = tail;
        tail.prev = head;
    }
    public int get(int key) {
        if (!map.containsKey(key)) return -1;
        Node node = map.get(key);
        remove(node);
        insert(node);
        return node.value;
    }
    public void put(int key, int value) {
        if (map.containsKey(key)) {
            remove(map.get(key));
        }
        if (map.size() == capacity) {
            map.remove(tail.prev.key);
            remove(tail.prev);
        }
        Node node = new Node(key, value);
        insert(node);
        map.put(key, node);
    }
    private void remove(Node node) {
        node.prev.next = node.next;
        node.next.prev = node.prev;
    }
    private void insert(Node node) {
        node.next = head.next;
        node.prev = head;
        head.next.prev = node;
        head.next = node;
    }
}
