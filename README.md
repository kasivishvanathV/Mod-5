# CPP MODULE 5 :

# 5a :

# PROGRAM STATEMENT :
Write a CPP Program to insert five character elements in to Stack ADT (use STL for Stack)

# ALGORITHM :
1. Include the necessary header files (<stack> and <iostream>) and define the main function.
2. Create a stack of character using std::stack<int> from the Standard Template Library (STL).
3. Use a loop to insert five character elements into the stack using the push() function.
4. Display the stack elements by popping them one by one using the pop() function inside a loop.
5. End the program after all elements are removed and displayed.
# PROGRAM :
NAME : V.Kasivishvanath
REG NO : 212222040073
```
#include <iostream>
#include <stack>
using namespace std;
int main() 
{
 int n;
 cin>>n;
 stack<char> stk;
 char ch;
 for (int i = 0; i < n; ++i)
 {
 cin >> ch;
 stk.push(ch);
 }
 cout << "Size of the stack: " << stk.size() << endl;
 while (!stk.empty())
 {
 cout << stk.top() << " ";
 stk.pop();
 }
 
 cout << endl;
 return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/304d8ca5-b7a7-4263-9565-2d4926209328)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 5b :

# PROGRAM STATEMENT :
Write a CPP program for Postfix to Prefix Conversion using Stack STL

# ALGORITHM :
1. Read the infix expression as a string from the user.
2. Reverse the infix expression and replace '(' with ')' and vice versa to prepare for prefix conversion.
3. Use the infixToPostfix() function to convert the modified expression to postfix notation.
4. Reverse the resulting postfix expression to get the prefix expression.
5. Print the final prefix expression.

# PROGRAM :
```
#include<bits/stdc++.h>
using namespace std;
bool isOperator(char c)
{
 return(!isalpha(c)&& !isdigit(c));
}
int getPriority(char C)
{
 if(C =='-'||C=='+')
 return 1;
 else if(C =='*'||C=='/')
 return 2;
 else if(C=='^')
 return 3;
 return 0;
}
string infixToPostfix(string infix)
{
 infix='('+ infix +')';
 int l=infix.size();
 stack<char>char_stack;
 string output;
 for(int i=0; i<l;i++)
 {
 if(isalpha(infix[i])||isdigit(infix[i]))
 output+=infix[i];
 else if(infix[i]=='(')
 char_stack.push('(');
 else if(infix[i]==')')
 {
 while(char_stack.top()!='(')
 {
 output+=char_stack.top();
 char_stack.pop();
 }
 char_stack.pop();
 }
 else
 {
 if (isOperator(char_stack.top()))
 {
 if(infix[i] =='^')
 {
 while(getPriority(infix[i])<=getPriority(char_stack.top()))
 {
 output+=char_stack.top();
 char_stack.pop();
 }
 }
 else
 {
 while(getPriority(infix[i])<getPriority(char_stack.top()))
 {
 output+=char_stack.top();
 char_stack.pop();
 }
 }
 char_stack.push(infix[i]);
 }
 }
 }
 while(!char_stack.empty())
 {
 output+=char_stack.empty();
 char_stack.pop();
 }
 return output;
}
string infixToPrefix(string infix)
{
 int l=infix.size();
 reverse(infix.begin(),infix.end());
 for(int i=0; i<l;i++)
 {
 if(infix[i]=='(')
 {
 infix[i]='}';
 i++;
 }
 }
 string prefix=infixToPostfix(infix);
 reverse(prefix.begin(),prefix.end());
 return prefix;
}
int main()
{
 string s;
 cin>>s;
 cout<<"Prefix expression: ";
 cout<<infixToPrefix(s);
 return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/63f8da28-0e21-46d9-b44d-5a27eadc8ffa)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 5c :

# PROGRAM STATEMENT :
Write a CPP Program to insert five character elements in to Queue ADT (use STL for Queue)

# ALGORITHM :
1. Include necessary header files (<queue> and <iostream>) and define the main function.
2. Create a queue of character using std::queue<float> from the Standard Template Library (STL).
3. Use a loop to insert five character elements into the queue using the push() function.
4. Display the queue elements by accessing and removing them one by one using the front() and pop() 
functions inside a loop.
5. End the program after all elements are removed and displayed.

# PROGRAM :
```
#include <iostream>
#include <queue>
using namespace std;
int main()
{
 queue<char> myQueue;
 char element;
 
 for (int i = 0; i < 5; ++i)
 {
 cin >> element;
 myQueue.push(element);
 }
 
 cout << "Queue Elements are:";
 
 while (!myQueue.empty()) 
 {
 cout << myQueue.front() << " ";
 myQueue.pop();
 }
 
 cout << endl;
 return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/b9e0589d-5b02-4772-938c-0aa5f582b9fe)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.

# 5d :

# PROGRAM STATEMENT :
write a C++ program to implement FCFS algorithm(no of.process p1,p2 and p3 and its burst time 
are 10,5 & 8) find out waiting time & Turn Around time of the the process?

# ALGORITHM :
1. Input the number of processes, process IDs (P1, P2, P3), and their respective burst times (10, 5, and 
8).
2. Initialize waiting time (WT) of the first process as 0 and calculate waiting time for subsequent 
processes as WT[i] = WT[i-1] + Burst[i-1].
3. Compute Turnaround Time (TAT) for each process as TAT[i] = WT[i] + Burst[i].
4. Display the processes, their burst times, waiting times, and turnaround times.
5. Calculate and display the average waiting time and turnaround time, then end the program.

# PROGRAM :
```
#include <iostream>
using namespace std;
void calculateWaitingTime(int bt[], int n, int wt[]) 
{
 wt[0] = 0; 
 
 for (int i = 1; i < n; i++)
 {
 wt[i] = wt[i - 1] + bt[i - 1];
 }
}
void calculateTurnAroundTime(int bt[], int wt[], int n, int tat[]) 
{
 for (int i = 0; i < n; i++)
 {
 tat[i] = bt[i] + wt[i];
 }
}
void displayResults(int bt[], int wt[], int tat[], int n) 
{
 cout << "Processes BT time WT time TA time\n";
 
 for (int i = 0; i < n; i++)
 {
 cout << " " << i + 1 << " " << bt[i] << " " << wt[i] << " " << tat[i] << endl;
 }
}
int main() 
{
 int n = 3; 
 int bt[] = {10, 5, 8}; 
 int wt[n], tat[n]; 
 
 calculateWaitingTime(bt, n, wt);
 calculateTurnAroundTime(bt, wt, n, tat);
 displayResults(bt, wt, tat, n);
 return 0;
}
```

# OUTPUT :
 ![image](https://github.com/user-attachments/assets/b09866de-fb25-4e92-8dd7-993cacfc558d)

# RESULT :
Thus, The program is verified and executed successfully.The outputs match the expected 
results, confirming its correctness.
