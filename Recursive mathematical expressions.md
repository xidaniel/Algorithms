# Recursion Types
  [reference](https://www.geeksforgeeks.org/types-of-recursions/)
  - Master Theorem
    - T(n) = a * T(n/b) + f(n)
      - T(n): Scale of problem
      - a: Number of sub-problems
      - T(n/b): Scale of sub-problems
      - f(n): Number of merge operations
    - Example:
    
        | Equation                               | Time              | Space          | Example               |
        |----------------------------------------|-------------------|----------------|-----------------------|
        | T(n) = 2 * T(n/2) + f(n)               | O(nlogn) ~ O(n^2) | O(logn) ~ O(n) | Quick sort            |
        | T(n) = 2 * T(n/2) + f(n)               | O(nlogn)          | O(n + logn)    | Merge sort            |
        | T(n) = T(n/2) + f(1)                   | O(logn)           | O(logn)        | Binary search         |
        | T(n) = 2 * T(n/2) + f(1)               | O(n)              | O(logn) ~ O(n) | Binary tree traversal |
        | T(n) = n * T(n - 1)                    | O(n!)             | O(n)           | Permutation           |
        | T(n) = T(n - 1) + T(n - 2) + ...+ T(1) | O(2^n)            | O(n)           | Combination           |
  
  - Tail Recursion:
    - If a recursive function calling itself and that recursive call is the last statement in the function then it’s known as Tail Recursion.After that call the recursive function performs nothing. The function has to process or perform any operation at the time of calling and it does nothing at returning time.
    - Codeing Example:
      
          def fun(n):
            if n > 0:
              print(n)
              fun(n - 1) 
              
          Input: fun(3)
          Output: 3, 2, 1
    
  - Head Recursion:
    - If a recursive function calling itself and that recursive call is the first statement in the function then it’s known as Head Recursion.There’s no statement, no operation before the call. The function doesn’t have to process or perform any operation at the time of calling and all operations are done at returning time.
    - Codeing Example:
    
          def fun(n):
            if n > 0:
              fun(n - 1)
              print(n)
              
          Input: fun(3)
          Output: 1, 2, 3
    
  - Tree Recursion:
    - If a recursive function calling itself for one time then it’s known as Linear Recursion. Otherwise if a recursive function calling itself for more than one time then it’s known as Tree Recursion.
    - Codeing Example:
    
          def fun(n):
            if n > 0:
              print(n)
              fun(n - 1)
              fun(n - 1)
              
          Input: fun(3)
          Output: 3, 2, 1, 1, 2, 1, 1
    
  - Nested Recursion:
    - In this recursion, a recursive function will pass the parameter as a recursive call.That means “recursion inside recursion”. 
    - Codeing Example:
    
          def fun(n):
            if n > 100:
              return n - 10
            return fun(fun(n + 11))
            
          Input: fun(95)
          Output: 91
          
   - Indirect Recursion
     - In this recursion, there may be more than one functions and they are calling one another in a circular manner.
     - Codeing Example:
    
            def funA(n):
              if n > 0:
                print(n)
                funB(n - 1)

            def funB(n):
              if n > 1:
                print(n)
                fun(n / 2)

             Input: funA(20)
             Output: 20, 19, 9, 8, 4, 3, 1



# Dynamic-Programming
  - Base case
  - Induction rule
    - Find min question, consider from smaller question 
    - Find a table
   
## One dimension DP 
   - Fibonacci 
   - Long Asceding Sub-array
   - Maximum Product when Cutting Rope
   - Jump Game
   
## Two dimension DP 
