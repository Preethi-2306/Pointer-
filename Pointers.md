[POINTER] :- A pointer is a variable that stores the ADDRESS (location) of another variable.
Not “a location.”
Not “stores data.”
Not “stores value.”
ONLY the address.
(Before interviews / exams practise questions on pointers if u do that u will get the concpet aslo well)
Pointer reassignment means:You make the pointer POINT to someone else.
Example:int a = 5, b = 9;
int *p = &a;   // p -> a
p = &b;        // p -> b   (this is reassignment)
Pointer moves from a → b.
You didn’t change a or b here.
You only changed what p is pointing to.

Pointer: is a variable that stores the memory address of another variable, instead of storing a value directly.
1️⃣ &x → gives address of x: it means the address of the x 
2️⃣ p ->  holds the address of x (or whatever variable it points to)
3️⃣ *p → value stored at the address inside p: it when u want to access the actual data value at p then u will use this type of accessing
//so look dont get confused now p has x address right so whenver we use *p it means directky we are dealing with the x data value 

[format specifier]:- %p = “print an address (a pointer value)”
int age=22;
int *ptr=&age;  // so if age has address 1000 
1) printf("%p",&age); = prints the The address of the variable age  OUTPUT: 1000
2) printf("%p",ptr); = prints the address of age, because ptr is literally storing that address. OUTPUT: 1000
3)printf("%p",&ptr); = It is the address where the pointer variable itself is stored (because ptr is also a variable and itself has an address imagine it has 2000 so the output :2000 ) 
4)printf("%d",*(&age)); = so if &age is 1000 and *1000 means it goes to the address and it points to 22 so OUTPUT :- 22

->  WE CAN EVEN ASSIGN VALUE INDERCTLY TO VARAIBLE BY ASSINING TO THE POINTER ADDRESS
#include <stdio.h>
int main() {
    int y;
    int *pulp;
    
    pulp=&y;
    *pulp=0;
    printf("%d\n",y);
    printf("%d\n",*pulp);

    return 0;
} OUTPUT: 0
          0
// HERE we are assign the value 0 to *pulp means it sould return a data value, so we are assigning address of y in pulp  right so it goes to *pulp which has the address of y right so from there it goes to y and gets stored as 0
EXAMPLE:- 
#include <stdio.h>
int main() {
    
    int a=10;  // assigning int value to a 
    int *pulp=&a;  //now assigning the address of a to an pointer called pulp 
    int b=*pulp;  // and now just access the data value at *pulp which internal store the address of a right,so it goes to address of a and give the values of a and stores the value 10 in b
    printf("%d",b);  // output : 10  
    return 0;
}

[POINTER TO POINTER]:- Like how a pointer stores address of another variable, this pointer to poiter stores the address of another pointer.

->So **ptr holds the address of the ptr pointer and and forms like a circle, where the first(*ptr)=goes to address of i and give the value 5 , and (*pptr)= goes to address of the ptr and (**ptr) goes to the value of i which gives 5 <img width="789" height="393" alt="image" src="https://github.com/user-attachments/assets/de55a75a-1e41-4c3a-8733-6cf874793d69" />
-> Though, pointer to pointer is not regularly used, still we need to undestand it for interview question and should know the working and difference between the (* and ** and & ).

Using pointers allows a function to modify variables from the caller, because the function receives their addresses instead of copies. C normally passes values by copy, so without pointers the function cannot change the original variables and can also return only one value. By passing addresses to sum, prod, and avr, the function directly writes results into the actual variables in main, avoiding copies and allowing multiple outputs.

[POINTERS IN FUNCTION CALL] :- there are two types 
1) CALL BY VALUE:- we pass value of the variable as argument 
It is observed when you call an function, the value is just passed by to function definition / only the values's copy is sent not the original value ex: square of a number
#include <stdio.h>
void square(int n);

int main() {
    int num=4;
    square(num);
    printf("num original value is =%d\n",num);
    
    return 0;
}
void square(int n){
    n=n*n;
    printf("square of the value is =%d\n",n);
}    
OUTPUT : square of the value is = 16
         num original value is = 4 

2)[CALL BY REFERENCE]:-WE pass address of varaible as argument
 here what happens is unlike pass by value here we take the address of the variable directly and perform on that so now it will change the direct values in the address .-> we perfom operation like (*n) * (*n) so since in value at it will go to num address which has 4 and does this 4*4 and return the 16 as original number.
 -> The value changes permenantely inside the address, beause this adress is only present in the the pointer we made operation on.
 -> we use these when we want to rrturn too many values from a function we use pointers,
<img width="464" height="230" alt="image" src="https://github.com/user-attachments/assets/af557460-1626-429b-98be-f8480324bcab" /> example :-
#include <stdio.h>
void square(int n);

void _square(int *n);

int main() {
    int num=4;
    square(num);
    printf("num original value is =%d\n",num);
   
    _square(&num);
    printf("num original value is =%d\n",num);
    return 0;
}
void square(int n){
    n=n*n;
    printf("square of the value is =%d\n",n);
}
void _square(int *n){
    *n=(*n)*(*n);
    printf("square of the value is =%d\n",*n);
} output :- square of the value is =16
            num original value is =4
            square of the value is =16
            num original value is =16

[EXAMPLE 2] chech if the output adrress will be same or not <img width="431" height="306" alt="image" src="https://github.com/user-attachments/assets/1e48fb75-80a1-4067-acb5-8079326497b5" /> it will be not be same beacue is is call by value so the original and copy address would be different .
-> CALL BY REFERENCE
<img width="447" height="233" alt="image" src="https://github.com/user-attachments/assets/156b0e0a-b10b-4a0a-9c92-7306b1c09d28" /> this will result bothe adress as same
[EXAMPLE 3]:- do sum,product and average and print in main function
#include <stdio.h>

int work(int a, int b,int *sum,int*prod,int*avr);
int main() {
int a=2,b=5;
  int sum,prod,avr;
  
work(a,b,&sum,&prod,&avr);
printf("s=%d\n p=%d\n a=%d\n",sum,prod,avr);
    return 0;
}
int work(int a, int b,int *sum,int*prod,int*avr){
     *sum=a+b;
     *prod=a*b;
    *avr=(a+b)/2;
    
}
ourput : s=7
p=10
a=3
[ARRAY OPERATIONS USING POINTER]:-
->To access elements using a pointer, both x[i] and *(x + i) are valid.
*(x + i) is the pointer arithmetic form,
x[i] is just the shorter form.

-> You are doing pointer arithmetic.
x is a pointer to the first element.
i is the index.
x + i moves the pointer i steps forward.
*(x + i) reads the value at that new location.
 
 EXAMPLE :- #include <stdio.h>
void array(int *a,int n);

int main() {
int a[]={2,3,4,5,6};
int size=sizeof(a)/sizeof(a[0]);
array(a,size);
    return 0;
}
void array(int *a,int n){
    int i;
    for(i=n-1;i>=0;i--){
    printf("%d",*(a+i));
}
} output is 65432







            





