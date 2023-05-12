# Parallel Linked List
This is a C++ implementation of a parallel linked list. It provides concurrent access to the list by using mutex locks to ensure thread safety.

## Features
* Node class represents a node in the linked list and contains a key-value pair.
* Add function adds a new node to the list while maintaining the sorted order of keys.
* Contains function searches for a key in the list and prints its corresponding value if found.
* Remove function removes a node with a given key from the list.
* Print function prints the contents of the linked list to a file named "result.txt".
* ARTest and RATest are helper functions for testing concurrent add and remove operations.
## Usage
* Include the necessary headers:
```cpp
#include <iostream>
#include <mutex>
#include <thread>
#include <vector>
#include <fstream>
```

* Create an instance of the Node class to serve as the head of the linked list:
```cpp 
auto head = new Node(0, 0);
```
* Perform operations on the linked list:
  * Adding nodes:
```cpp 
Node* node = new Node(key, value);
Add(head, node);

```
  * Searching for a key:
 ```cpp
int keyToFind = 42;
Contains(head, keyToFind);
```
  * Removing a node:

```cpp
int keyToRemove = 42;
Remove(head, keyToRemove);

```
  * Printing the contents of the list:
```cpp
Print(head);

```
* Create threads to perform concurrent operations on the linked list:
```cpp
std::vector<std::thread> threads;
for (int i = 0; i < numThreads; ++i) {
    // Create nodes and perform operations
    threads.emplace_back(Add, head, node);
    threads.emplace_back(Remove, head, key);
}
for (auto& thread : threads) {
    thread.join();
}

```
### Note: Make sure to join all the threads before exiting the program to avoid termination issues.
