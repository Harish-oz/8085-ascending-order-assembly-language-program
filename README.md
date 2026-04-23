Here is the assembly language program Program to sort numbers in ascending order for microprocessor 8085.  
<br>
<br>
```
MVI B, 05H        ; B is number of passes, We repeat passes to ensure all elements get sorted
                  ; Each pass pushes the largest element to the end

LP2: MVI C, 05H   ; C = comparisons per pass, We compare adjacent elements multiple times in one pass
     LXI H, 3000H ; Enter the numbers here

LP1: MOV A, M     ; Load current element into A
     INX H        ; Move pointer to next element
     MOV D, M     ; Store next element in D (for temporary storage)
     CMP D        ; Compare A with next element, this checks if order is correct
     JC SKIP      ; If A < D → already in correct order (ascending)
                  ; No swap needed, skip to next pair
     MOV M, A     ; If A > D → put bigger value ahead temporarily
                  ; This starts the swap process
     DCX H        ; Move back to previous position
                  ; Needed to complete swap properly
     MOV M, D     ; Place smaller value before larger one
                  ; Now correct order is achieved for this pair
     INX H        ; Restore pointer position for next comparison

SKIP: DCR C       ; Reduce comparison count
      JNZ LP1     ; Keep comparing until all adjacent pairs checked
      DCR B       ; Reduce pass count
      JNZ LP2     ; Repeat passes until array is fully sorted

      HLT         ; Stop
```
<br>
<br>
Explaination<br>
Ascending order means arranging numbers from smallest → largest.  
For Example:<br>
Unsorted:  5, 2, 8, 1<br>
Sorted:    1, 2, 5, 8<br>
<br>
Core Idea (Bubble Sort)<br>
Compare two adjacent elements
If the left element is bigger, swap them
Move one step forward and repeat
After one full pass → largest element goes to the end
Repeat passes until everything is sorted

Ascending order means arranging numbers from smallest → largest.
👉 Example:
Plain text
Unsorted:  3, 9, 1, 5  
Sorted:    1, 3, 5, 9
🧠 Core Idea
Look at two neighboring numbers
If left > right → swap
If left ≤ right → leave it
Repeat this again and again.
⚙️ What actually happens
Smaller numbers move toward the left
Bigger numbers get pushed to the right
After each pass → largest number settles at the end
📌 Example
Plain text
Start: 3, 9, 1, 5

Compare 3 & 9 → ok  
Compare 9 & 1 → swap → 3, 1, 9, 5  
Compare 9 & 5 → swap → 3, 1, 5, 9  

Next pass → fix remaining pairs  
Final → 1, 3, 5, 9
