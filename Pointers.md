[Pointer] is a variable that stores the memory address of another variable, instead of storing a value directly.
1️⃣ &x → gives address of x: it means the address of the x (*p=&x)
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
