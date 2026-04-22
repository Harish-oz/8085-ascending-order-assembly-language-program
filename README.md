Here is the assembly language program Program to sort numbers in ascending order for microprocessor 8085.  

Sort 5 numbers in ascending order. 
Memory starts at 3000H. 


```
MVI B, 05H        ; Outer loop count

LP3: MVI C, 05H   ; Inner loop count
     LXI H, 3000H ; Point to start of array

LP2: MOV A, M     ; Load first number
     INX H        ; Move to next
     MOV D, M     ; Load second number

     CMP D        ; Compare A with D
     JC SKIP      ; If A < D, no swap

     ; Swap
     MOV M, A     ; Put A in next location
     DCX H
     MOV M, D     ; Put D in previous location
     INX H

SKIP: DCR C       ; Decrement inner loop
      JNZ LP2

      DCR B       ; Decrement outer loop
      JNZ LP3

      HLT               ; Stop
