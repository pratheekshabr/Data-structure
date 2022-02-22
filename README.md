# Data-structure
****************
1.Binary Search<br>
***************
#include<stdio.h><br>

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
using namespace std;<br>
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
*******<br>
![Screenshot (21)](https://user-images.githubusercontent.com/97940277/154897408-96f889e9-9d61-4197-bee9-d3e66a887445.png)<br>
****************************
3.Array using Linked list.<br>
*****************************
#include<iostream.h><br>
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
Output:<br>
*******<br>	
![Screenshot (23)](https://user-images.githubusercontent.com/97940277/154898295-15a6bf31-fd14-43b7-b528-6d6300ad83c0.png)<br>
***************
4.Write a C++ Program to split the linked list into two in such a way that the given element ele must be the first node of second list.<br>
***************
#include<iostream.h><br>
using namespace std;<br>
struct Node{<br>
int value;<br>
struct Node *next;<br>
};<br>
struct Node* head = NULL;<br>
struct Node* sHead = NULL;<br>
struct Node* temp = NULL;<br>
void insert(int new_data){<br>
struct Node* new_node = new Node(); //(struct Node*)malloc(sizeof(struct Node));<br>
new_node->value = new_data;<br>
new_node->next = head;<br>
head = new_node;<br>
}<br>
int n;<br>
int ele;<br>
int splitIndex;<br>
int main(){<br>
int i,j;<br>
cout<<"Enter number of elements you want in the list\t";<br>
cin>>n;<br>
cout<<"Enter elements :" <<endl;<br>
for(i=0;i<n;i++){<br>
cin>>ele;<br>
insert(ele);<br>
}<br>
cout<<"\nList of elements : "<<endl;<br>
Node *t;<br>
t = head;<br>
while(t != NULL){<br>
cout<<t->value<<"\t";<br>
t = t->next;<br>
}<br>
cout<<"\n\nEnter the position you want the list to split ";<br>
cin>>splitIndex;<br>
while(splitIndex < 0 || splitIndex > n-1){<br>
cout<<"Invalid position. Try again."<<endl;<br>
cin>>splitIndex;<br>
}<br>
temp = head;<br>
for(i=0;i<=splitIndex;i++){<br>
if(i==splitIndex-1){<br>
Node *tN;<br>
tN = temp->next;<br>
sHead = tN;<br>
temp->next = NULL;<br>
break;<br>
}<br>
temp = temp->next;<br>
}<br>
temp = head;<br>
if(temp == NULL){<br>
cout<<"\nFirst list is empty"<<endl;<br>
}else{<br>
cout<<"\n\nFirst list element "<<endl;<br>
while(temp != NULL){<br>
cout<<temp->value<<"\t";<br>
temp = temp->next;<br>
}<br>
}<br>
temp = sHead;<br>
if(temp == NULL){<br>
cout<<"\nSecond list is empty"<<endl;<br>
}else{<br>
cout<<"\n\nSecond list elements "<<endl;<br>
while(temp != NULL){<br>
cout<<temp->value<<"\t";<br>
temp = temp->next;<br>
}<br>
}<br>
return 0;<br>
}<br>
Output:<br>
*******<br>
![Screenshot (24)](https://user-images.githubusercontent.com/97940277/154902019-cc4dad66-2d2a-41e2-81ea-3568ed9565a4.png)<br>![Screenshot (26)](https://user-images.githubusercontent.com/97940277/154902238-71b673b3-fc60-4212-b6bf-f6d24ef2b849.png)<br>
*************
5.Write a C++ program to implement BST to support the following operations<br>
Assume no duplicate elements while constructing the BST<br>
1.Given a key perform a search in the BST, if the key is found then display “key found”<br>
2.Insert an element into a BST<br>
3.Delete an element from a BST<br>
Display the tree using Inorder,Preorder and Postorder traversal methods<br>
*******************
# include <iostream> <br>
# include <cstdlib> <br>
using namespace std; <br>
struct node <br>
{ <br>
 int info; <br>
 struct node *left; <br>
 struct node *right;<br> 
}*root; <br>
class BST <br>
{ <br>
 public: <br>
 void find(int, node **, node **); <br>
 void find(int, node **, node **); <br>
 void find(int, node **, node **); <br>
  void insert(node *, node *);  <br>
   void del(int);  <br>
 void case_a(node *,node *);  <br>
 void case_b(node *,node *);  <br>
 void case_c(node *,node *);  <br>  
 void preorder(node *);  <br> <br>  
 void inorder(node *);  <br>
 void postorder(node *);  <br>
 void display(node *, int);  <br>
 BST()  <br>
 {  <br>
 root = NULL; 
 } 
}; 
int main() 
{ 
 int choice, num; 
 BST bst; 
 node *temp; 
 while (1) 
 { 
 cout<<"-----------------"<<endl; 
 cout<<"Operations on BST"<<endl; 
 cout<<"-----------------"<<endl; 
 cout<<"1.Insert Element "<<endl; 
 cout<<"2.Delete Element "<<endl; 
 cout<<"3.Inorder Traversal"<<endl; 
 cout<<"4.Preorder Traversal"<<endl; 
 cout<<"5.Postorder Traversal"<<endl; 
 cout<<"6.Display"<<endl; 
 cout<<"7.Quit"<<endl; 
 cout<<"Enter your choice : "; 
 cin>>choice; 
 switch(choice) 
 { 
 case 1: 
 temp = new node; 
 cout<<"Enter the number to be inserted : "; 
 cin>>temp->info; 
 bst.insert(root, temp); 
 break; 
 case 2: 
 if (root == NULL) 
 { 
 cout<<"Tree is empty, nothing to delete"<<endl; 
 continue; 
 } 
 cout<<"Enter the number to be deleted : "; 
 cin>>num; 
 bst.del(num); 
 break; 
 case 3: 
 cout<<"Inorder Traversal of BST:"<<endl; 
 bst.inorder(root); 
 cout<<endl; 
 break; 
 case 4: 
 cout<<"Preorder Traversal of BST:"<<endl; 
 bst.preorder(root); 
 cout<<endl; 
 break; 
 case 5: 
 cout<<"Postorder Traversal of BST:"<<endl; 
 bst.postorder(root); 
 cout<<endl; 
 break; 
 case 6: 
 cout<<"Display BST:"<<endl; 
 bst.display(root,1); 
 cout<<endl; 
 break; 
 case 7: 
 exit(1); 
 default: 
 cout<<"Wrong choice"<<endl; 
 } 
 } 
} 
void BST::find(int item, node **par, node **loc) 
{ 
 node *ptr, *ptrsave; 
 if (root == NULL) 
 { 
 *loc = NULL; 
 *par = NULL; 
 return; 
 } 
 if (item == root->info) 
 { 
 *loc = root; 
 *par = NULL; 
 return; 
 } 
 if (item < root->info) 
 ptr = root->left; 
 else 
 ptr = root->right; 
 ptrsave = root; 
 while (ptr != NULL) 
 { 
 if (item == ptr->info) 
 { 
 *loc = ptr; 
 *par = ptrsave; 
 return; 
 } 
 ptrsave = ptr; 
 if (item < ptr->info) 
 ptr = ptr->left; 
 else 
 ptr = ptr->right; 
 } 
 *loc = NULL; 
 *par = ptrsave; 
} 

void BST::insert(node *tree, node *newnode) 
{ 
 if (root == NULL) 
 { 
 root = new node; 
 root->info = newnode->info; 
 root->left = NULL; 
 root->right = NULL; 
 cout<<"Root Node is Added"<<endl; 
 return; 
 } 
 if (tree->info == newnode->info) 
 { 
 cout<<"Element already in the tree"<<endl; 
 return; 
 } 
 if (tree->info > newnode->info) 
 { 
 if (tree->left != NULL) 
 { 
 insert(tree->left, newnode); 
 } 
 else 
 { 
 tree->left = newnode; 
 (tree->left)->left = NULL; 
 (tree->left)->right = NULL; 
 cout<<"Node Added To Left"<<endl; 
 return; 
 } 
 } 
 else 
 { 
 if (tree->right != NULL) 
 { 
 insert(tree->right, newnode); 
 } 
 else 
 { 
 tree->right = newnode; 
 (tree->right)->left = NULL; 
 (tree->right)->right = NULL; 
 cout<<"Node Added To Right"<<endl; 
 return; 
 } 
 } 
} 

void BST::del(int item) 
{ 
 node *parent, *location; 
 if (root == NULL) 
 { 
 cout<<"Tree empty"<<endl; 
 return; 
 } 
 find(item, &parent, &location); 
 if (location == NULL) 
 { 
 cout<<"Item not present in tree"<<endl; 
 return; 
 } 
 if (location->left == NULL && location->right == NULL) 
 case_a(parent, location); 
 if (location->left != NULL && location->right == NULL) 
 case_b(parent, location); 
 if (location->left == NULL && location->right != NULL) 
 case_b(parent, location); 
 if (location->left != NULL && location->right != NULL) 
 case_c(parent, location); 
 free(location); 
} 
 

void BST::case_a(node *par, node *loc ) 
{ 
 if (par == NULL) 
 { 
 root = NULL; 
 } 
 else 
 { 
 if (loc == par->left) 
 par->left = NULL; 
 else 
 par->right = NULL; 
 } 
} 
 

void BST::case_b(node *par, node *loc) 
{ 
 node *child; 
 if (loc->left != NULL) 
 child = loc->left; 
 else 
 child = loc->right; 
 if (par == NULL) 
 { 
 root = child; 
 } 
 else 
 { 
 if (loc == par->left) 
 par->left = child; 
 else 
 par->right = child; 
 } 
} 
 

void BST::case_c(node *par, node *loc) 
{ 
 node *ptr, *ptrsave, *suc, *parsuc; 
 ptrsave = loc; 
 ptr = loc->right; 
 while (ptr->left != NULL) 
 { 
 ptrsave = ptr; 
 ptr = ptr->left; 
 } 
 suc = ptr; 
 parsuc = ptrsave; 
 if (suc->left == NULL && suc->right == NULL) 
 case_a(parsuc, suc); 
 else 
 case_b(parsuc, suc); 
 if (par == NULL) 
 { 
 root = suc; 
 } 
 else 
 { 
 if (loc == par->left) 
 par->left = suc; 
 else 
 par->right = suc; 
 } 
 suc->left = loc->left; 
 suc->right = loc->right; 
} 
 
 
void BST::preorder(node *ptr) 
{ 
 if (root == NULL) 
 { 
 cout<<"Tree is empty"<<endl; 
 return; 
 } 
 if (ptr != NULL) 
 { 
 cout<<ptr->info<<" "; 
 preorder(ptr->left); 
 preorder(ptr->right); 
 } 
} 

void BST::inorder(node *ptr) 
{ 
 if (root == NULL) 
 { 
 cout<<"Tree is empty"<<endl; 
 return; 
 } 
 if (ptr != NULL) 
 { 
 inorder(ptr->left); 
 cout<<ptr->info<<" "; 
 inorder(ptr->right); 
 } 
} 
 
void BST::postorder(node *ptr) 
{ 
 if (root == NULL) 
 { 
 cout<<"Tree is empty"<<endl; 
 return; 
 } 
 if (ptr != NULL) 
 { 
 postorder(ptr->left); 
 postorder(ptr->right); 
 cout<<ptr->info<<" "; 
 } 
} 
 
void BST::display(node *ptr, int level) 
{ 
 int i; 
 if (ptr != NULL) 
 { 
 display(ptr->right, level+1); 
 cout<<endl; 
 if (ptr == root) 
 cout<<"Root->: "; 
 else 
 { 
 for (i = 0;i < level;i++) 
 cout<<" "; 
 } 
 cout<<ptr->info; 
 display(ptr->left, level+1); 
 } 
}













