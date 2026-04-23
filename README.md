Here is the assembly language program Program to sort numbers in ascending order for microprocessor 8085.  
<br>
<br>
```
MVI B, 05H        ; B is number of passes, We repeat passes to ensure all elements get sorted
                  ; Each pass pushes the largest element to the end

LP2: MVI C, 05H   ; C is comparisons per pass, We compare adjacent elements multiple times in one pass
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
<br><br><br>
**Explanation**<br>
Ascending order means arranging numbers from smallest → largest.<br>
For example<br>
Unsorted:  3, 9, 1, 5<br>
Sorted:    1, 3, 5, 9<br>
<br>
<br>
Look at two neighboring numbers<br>
If left > right → swap<br>
If left ≤ right → leave it<br>
<br>
Repeat this again and again.<br>
Smaller numbers move toward the left and bigger numbers get pushed to the right. After each pass → largest number settles at the end<br>
<br>
<br>
**For Example**<br>
Start: 3, 9, 1, 5<br>
Compare 3 & 9 → ok<br>
Compare 9 & 1 → swap → 3, 1, 9, 5<br>
Compare 9 & 5 → swap → 3, 1, 5, 9<br>
<br>
Next pass → fix remaining pairs<br>
Final → 1, 3, 5, 9<br>
