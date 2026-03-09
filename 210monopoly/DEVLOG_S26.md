# Developer Log (DEVLOG.md)
## Monopoly Board Simulator (Spring 2026)

Minimum **6 entries** required.

Each entry must document learning and reasoning. Fabricated bugs are not expected.

---

## Allowed Entry Types
Each entry may be one of the following:

1) **Bug Fix Entry**
- The issue encountered.
- Error messages or symptoms.
- Attempts made.
- Final resolution.

2) **Edge Case / Testing Entry**
- A failure discovered through testing.
- The specific input/state that caused it.
- The change you made to handle it correctly.

3) **Engineering Decision Entry (up to 2 allowed)**
- A design decision you made.
- An alternative approach you considered.
- Why you chose one approach over another (tradeoffs).

---

### Entry 1
**Date:** 2026-03-05 
**Entry Type:** Bug Fix  
**Task worked on:**: Core A: addSpace()
**Issue or decision:**: Linked list wasn't set correctly when adding nodes; changed ->nextNode to ->next
**Error message / symptom (if applicable):**: Compile error: class Node has no member named 'next'
**What I tried:**: Mistook the pointer field for next and traced the erorr back to the Node class definition
**Fix / resolution (or final decision):**: changed every instance of ->next to ->nextNode
**Commit(s):**  fix nextNode pointer name in addSpace

---

### Entry 2
**Date:** 2026-03-06  
**Entry Type:** Bug Fix 
**Task worked on:**: Code D: printFromPlayer()
**Issue or decision:**: Compile error
**Error message / symptom (if applicable):**'currentNode' not declared in this scope
**What I tried:**  : Originally tried to write the loop with currentNode as if it was a class member
**Fix / resolution (or final decision):**: Declared local playerNode before the loop and changed currentNode to curr->
**Commit(s):**: fix printFromPlayer using playerNode

---

### Entry 3
**Date:** 2026-03-06  
**Entry Type:** Bug Fix 
**Task worked on:**: Advanced A removeByName()
**Issue or decision:** : after finding and relinking the matched mode I forgot to delete curr, subtract nodeCount by 1 and return true. The function was returning false even when deletetion worked. 
**Error message / symptom (if applicable):** 
**What I tried:**  When manually tracing I saw the control reach prev = curr and curr = curr->nextNode even when it matched 
**Fix / resolution (or final decision):**: Added delete curr, nodecount--, and return true to update head and tail pointers and exit correctly after removal
**Commit(s):**: corrected removeByName logic  

---

### Entry 4
**Date:** 2026-03-06  
**Entry Type:** Edge Case  
**Task worked on:**: Advanced A  
**Issue or decision:**: When the list only had one node and removeByName was called the code tried to set playerNode = curr->next Node before checking for single nodes  
**Error message / symptom (if applicable):**  
**What I tried:** : Added print statement to confirm playerNode was pointing to freed memory after the call 
**Fix / resolution (or final decision):**: Moved nodeCount ==1 at the top of the match block  
**Commit(s):** : fix single node handling in removeByName to avoid dangling node

---

### Entry 5
**Date:** 2026-03-08  
**Entry Type:** Engineering Decision  
**Task worked on:** : Advanced A: find ByColor() 
**Issue or decision:** : Had to choose to use a do while or for loop to traverse the list one time 
**Error message / symptom (if applicable):**  
**What I tried:**: tried using a for loop to traverse i from 0 to nodeCount  
**Fix / resolution (or final decision):**: Chose a do while curr!= headNode because it relies on the circular list structure instead of a variable counter  
**Commit(s):**  : fix findByColor()

---

### Entry 6
**Date:** 2026-03-08  
**Entry Type:** Bug Fix 
**Task worked on:**: Optional helper printBoardOnce()  
**Issue or decision:**: called curr-print() on the node pointer when the node class doesn't have a print() method  
**Error message / symptom (if applicable):**: 'Node<MonopolySpace> has no member named 'print'  
**What I tried:** : I thought the template class forwarded calls by itself but saw that the node class definition only has data and nextNode class members. 
**Fix / resolution (or final decision):**: changed curr->print() to curr->data.print() so it reaches the print() method of the node's data field   
**Commit(s):**: fix printBoardOnce  
