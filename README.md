# Data-structure
****************
1.Binary Search<br>
***************
#include <stdio.h><br>

int main()<br>
{<br>
  int c, first, last, middle, n, search, array[100];<br>
  printf("Enter number of elements\n");<br>
  scanf("%d", &n);<br>
  printf("Enter %d integers\n", n);<br>
  for (c = 0; c < n; c++)<br>
    scanf("%d", &array[c]);<br>
  printf("Enter value to find\n");<br>
  scanf("%d", &search);<br>
  first = 0;<br>
  last = n - 1;<br>
  middle = (first+last)/2;<br>
  while (first <= last) {<br>
    if (array[middle] < search)<br>
      first = middle + 1;<br>
    else if (array[middle] == search) {<br>
      printf("%d found at location %d.\n", search, middle+1);<br>
      break;<br>
    }<br>
    else<br>
      last = middle - 1;<br>
    middle = (first + last)/2;<br>
  }<br>
  if (first > last)<br>
    printf("Not found! %d isn't present in the list.\n", search);<br>
  return 0;<br>
}<br>
output:<br>
*********<br>

![Screenshot (18)](https://user-images.githubusercontent.com/97940277/154893532-ad5d1e8f-56f2-419f-b980-0b3c800ea959.png)<br>
***********************
2.Stack using Array<br>
***********************

#include<stdio.h><br>
int stack[100],choice,n,top,x,i;<br>
void push(void);<br>
void pop(void);<br>
void display(void);<br>
int main()<br>
{<br>
    top=-1;<br>
    printf("\n Enter the size of STACK : ");<br>
    scanf("%d",&n);<br>
    printf("\n STACK OPERATIONS USING ARRAY");<br>
    printf("\n 1.PUSH\n 2.POP\n 3.DISPLAY\n 4.EXIT");<br>
    do<br>
    {<br>
        printf("\n Enter the Choice:");<br>
        scanf("%d",&choice);<br>
        switch(choice)<br>
        {<br>
            case 1:<br>
            {
                push();<br>
                break;<br>
            }<br>
            case 2:<br>
            {<br>
                pop();<br>
                break;<br>
            }<br>
            case 3:<br>
            {<br>
                display();<br>
                break;<br>
            }<br>
            case 4:<br>
            {<br>
                printf("\nExiting...");<br>
                break;<br>
           }<br>
           default:<br>
           {<br>
             printf ("\n Please Enter a Valid Choice(1/2/3/4)");<br>
   }<br>
                
  }<br>
 }<br>
    while(choice!=4);<br>
    return 0;<br>
}<br>
void push()<br>
{<br>
    if(top>=n-1)<br>
    {<br>
      printf("\nSTACK is over flow");<br>
         
   }<br>
   else<br>
   {<br>
       printf(" Enter a value to be pushed:");<br>
       scanf("%d",&x);<br><br>
       top++;<br>
       stack[top]=x;<br>
    }<br>
}<br>
void pop()<br>
{<br>
    if(top<=-1)<br>
    {<br>
       printf("\n Stack is under flow");<br>
    }<br>
    else<br>
    {<br>
       printf("\nThe popped elements is %d",stack[top]);<br>
       top--;<br>
    }<br>
}<br>
void display()<br>
{<br>
    if(top>=0)<br>
    {<br>
       printf("\n The elements in STACK \n");<br>
       for(i=top; i>=0; i--)<br>
       printf("\n%d",stack[i]);<br>
       printf("\n Enter Next Choice");<br>
    }<br>
    else<br>
    {<br>
        printf("\n The STACK is empty");<br>
    }<br>
}<br>

Output:<br>
![Screenshot (21)](https://user-images.githubusercontent.com/97940277/154897408-96f889e9-9d61-4197-bee9-d3e66a887445.png)<br>
****************************
3.Array using Linked list.<br>
*****************************
#include <iostream><br>
using namespace std;<br>

// Representation of a node
struct Node {<br>
	int data;<br>
	Node* next;<br>
};<br>

// Function to insert node
void insert(Node** root, int item)<br>
{<br>
	Node* temp = new Node;<br>
	Node* ptr;<br>
	temp->data = item;<br>
	temp->next = NULL;<br>
	if (*root == NULL)<br>
		*root = temp;<br>
	else {<br>
		ptr = *root;<br>
		while (ptr->next != NULL)<br>
			ptr = ptr->next;<br>
		ptr->next = temp;<br>
	}<br>
}<br>

void display(Node* root)<br>
{
	while (root != NULL) {<br>
		cout << root->data << " ";<br>
		root = root->next;<br>
	}<br>
}<br>

Node *arrayToList(int arr[], int n)<br>
{<br>
	Node *root = NULL;<br>
	for (int i = 0; i < n; i++)<br>
		insert(&root, arr[i]);<br>
return root;<br>
}<br>

// Driver code
int main()<br>
{<br>
	int arr[] = { 1, 2, 3, 4, 5 };<br>
	int n = sizeof(arr) / sizeof(arr[0]);<br>
	Node* root = arrayToList(arr, n);<br>
	display(root);<br>
	return 0;<br>
}<br>





