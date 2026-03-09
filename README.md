Jasper McIntyre

3/4/2026

Data Structures

Programming Assignment 1

BUILD AND RUN INSTRUCTIONS:

requirements: C++ compiler
1) compile the cpp file
2) run monopoly.cpp

DATA STRUCTURES

CircularLinkedList<T>: A circular singly linked list that represents the monopoly game board. Every node's nextNode pointer links back to the head forming the circle. This is what makes repetitive player traversal possible.

Node<T>: Node class that holds data with T field type and nextNode pointer to the next node in the list

MonopolySpace: The data class inside each node that stores string propertyName, string propertyColor, int value, and int rent.

vector<MonopolySpace>: Used to collect all 40 spaces when the board is created and adds them to the circular list through addMany

40 SPACE LIMIT
The board has an unchangable maximum of 40 spaces per board like the game in real life, stored in the constant: static const int MAX_SPACES = 40. If the board is full, addMany stops when addSpace is false to maintain the strict limit.

TRAVERSAL LOGIC
The player's position is stored in the playerNode pointer, which points to a node in the ring. When movePlayer is called, it moves playerNode forward one node steps times. After each step, if playerNode==headNode is true, the player has gone around the board one time and passGoCount increases by 1.

FUNCTION REFERENCE CHART
function; description

MonopolySpace
MonopolySpace(); default constructor; sets all fields to zero
MonopolySpace(name, color, value, rent); sets all fields
isEqual(MonopolySpace other); returns true if 2 spaces share the same propertyName
print(); prints the space's name, color, value, and rent

CircularLinedList<T>
CircularLinkedList(); constructor that initializes all pointers to nullptr and counters to 0
addSpace(T value); adds one node to the tail, returns true if successfull false if full
addMany(vector<T>> values); adds multiple spaces at a time and returns number of successfully added
movePlayer(int steps); increments playerNode by steps and tracks if passed GO
getPassGoCount(); returns how many times player passed GO
printFromPlayer(int count); prints count nodes from playerNode
printBoardOnce(); traverses and prints every node from head to tail once
removeByName(String name); deletes first node with matching name, handles head, tail, one node or playerNode cases; returns true if found
findByColor(string color); traverses ring once and returns vector of names with matching color
countSpaces(); counts nodes traversally
clear(); breaks the circular link, deletes all nodes, and resets all pointers/counters to 0
