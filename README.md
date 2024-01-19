# SLL
 operations on Singly Linked List (SLL) 
 #include<stdio.h> 
#include<stdlib.h> 
struct node // structure to create a NODE of Student info 
{ 
char usn[20],name[10],branch[5]; 
int sem,phno; 
struct node *link; 
}; 
typedef struct node * NODE; //rename node as NODE 
NODE temp,FIRST=NULL; // declare two structure variables 
NODE getnode() // Create a single node with DMA 
{ 
NODE x; 
x=(NODE)malloc(sizeof(struct node)); 
x->link=NULL; 
return x; 
} 
void read() // Read student details 
{ 
temp=getnode(); 
printf("Enter USN:\n"); 
scanf("%s",temp->usn); 
printf("Enter NAME\n"); 
scanf("%s",temp->name); 
printf("Enter Branch\n"); 
scanf("%s",temp->branch); 
printf("Enter Semester\n"); 
scanf("%d",&temp->sem); 
printf("Enter phno:\n"); 
scanf("%d",&temp->phno); 
} 
void create_SLL() // a. Create a SLL of N Students Data by using front insertion. 
{ 
int n,i; 
printf("Enter the number of students\n"); 
scanf("%d",&n); 
for(i=1;i<=n;i++) 
{ 
printf("\n Enter the details of %d students\n",i); 
read(); 
if(FIRST==NULL) 
FIRST=temp; 
else 
{ 
temp->link=FIRST; 
FIRST=temp; 
} 
} 
} 
void display_count() // b. Display the status of SLL and count the number of nodes 
in it 
{ 
int count=1; 
temp=FIRST; 
printf("Student details:\n"); 
if(FIRST==NULL) // check for empty list 
printf("Student detail is NULL and count is 0\n"); 
else 
{ 
printf("USN\tNAME\tBRANCH\tSEMESTER\tPHNO\n"); 
while(temp->link!=NULL) // repeate displaying NODE details until the end node. 
{ 
count++; 
printf("%s\t%s\t%s\t%d\t\t%d\n",temp->usn,temp->name,temp->branch,temp
>sem,temp->phno); 
temp=temp->link; 
} 
printf("%s\t%s\t%s\t%d\t\t%d",temp->usn,temp->name,temp->branch,temp
>sem,temp->phno); 
printf("\ntotal node count is %d\n",count); // display final count 
} 
return; 
} 
void insert_front() //c. Perform Insertion at the front of SLL 
{ 
printf("Enter the details of student\n"); 
read(); // read student details 
if(FIRST==NULL) // check for empty list if so concider new node as first node 
FIRST=temp; 
else // otherwise insert at front 
{ 
temp->link=FIRST; 
FIRST=temp; 
} 
} 
void insert_end() //Perform Insertion at the end of SLL 
{ 
NODE last=FIRST; 
printf("Enter the details of student\n"); 
read(); // read student details 
if(FIRST==NULL) // check for empty list if so concider new node as first node 
FIRST=temp; 
else // otherwise insert at end 
{ 
while(last->link!=NULL) // loop to reach last node 
last=last->link; 
last->link=temp; 
} 
} 
void delete_front() ////Perform deletion at the front of SLL 
{ 
temp=FIRST; 
if(FIRST==NULL) // check for empty list 
printf("List is empty\n"); 
else // otherwise delete front node 
{ 
printf("deleted element is %s\n",temp->usn); 
FIRST=FIRST->link; 
free(temp); 
} 
return; 
} 
void delete_end() //Perform Deletion at the end of SLL 
{ 
NODE last=NULL; 
temp=FIRST; 
if(FIRST==NULL) // check for empty list 
printf("List is empty\n"); 
else if(FIRST->link==NULL) // check for single node in list and delete 
{ 
printf("Deleted element is %s\n",temp->usn); 
free(FIRST); 
FIRST=NULL; 
} 
else // otherwise delete node from the end of list 
{ 
while(temp->link!=NULL) // loop to reach last node 
{ 
last=temp; 
temp=temp->link; 
} 
last->link=NULL; 
printf("Deleted element is %s\n",temp->usn); 
free(temp); 
} 
return; 
} 
void main() 
{ 
int choice; 
while(1) 
{ 
printf("1. Create SLL\n2.Display SSL\n3.Insert front\n4.Insert end\n5.Delete 
front\n6.Delete end\n7.EXIT\n"); 
printf("Enter your choice\n"); 
scanf("%d",&choice); 
switch(choice) 
{ 
case 1:create_SLL(); 
break; 
case 2:display_count(); 
break; 
case 3:insert_front(); 
break; 
case 4:insert_end(); 
break; 
case 5:delete_front(); 
break; 
case 6:delete_end(); 
break; 
case 7:return; 
default:printf("\nInvalid choice\n"); 
} // end of switch 
} // end of while 
} // end of main
