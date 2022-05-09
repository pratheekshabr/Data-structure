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
     # include <iostream> 
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
 root = NULL; <br> 
 } <br> 
}; <br> 
int main() <br> 
{ <br> 
 int choice, num; <br> 
 BST bst; <br> 
 node *temp; <br> 
 while (1) <br> 
 { 
 cout<<"-----------------"<<endl; <br> 
 cout<<"Operations on BST"<<endl; <br> 
 cout<<"-----------------"<<endl; <br> 
 cout<<"1.Insert Element "<<endl; <br> 
 cout<<"2.Delete Element "<<endl;<br> 
 cout<<"3.Inorder Traversal"<<endl; <br> 
 cout<<"4.Preorder Traversal"<<endl; <br> 
 cout<<"5.Postorder Traversal"<<endl; <br> 
 cout<<"6.Display"<<endl; <br> 
 cout<<"7.Quit"<<endl; <br> 
 cout<<"Enter your choice : "; <br> 
 cin>>choice; <br> 
 switch(choice) <br> 
 { <br> 
 case 1: <br> <br> 
 temp = new node; <br> 
 cout<<"Enter the number to be inserted : "; <br> 
 cin>>temp->info; <br> 
 bst.insert(root, temp); <br> 
 break; <br> 
 case 2: <br> 
 if (root == NULL) <br> 
 { <br> 
 cout<<"Tree is empty, nothing to delete"<<endl; <br> 
 continue; <br> 
 } <br> 
 cout<<"Enter the number to be deleted : "; <br> 
 cin>>num; <br> 
 bst.del(num); <br> 
 break; <br> 
 case 3: <br> 
 cout<<"Inorder Traversal of BST:"<<endl; <br> 
 bst.inorder(root); <br> 
 cout<<endl;<br>  
 break; <br> 
 case 4: <br> 
 cout<<"Preorder Traversal of BST:"<<endl; <br> 
 bst.preorder(root); <br> 
 cout<<endl; <br> 
 break;<br>  
 case 5: <br> 
 cout<<"Postorder Traversal of BST:"<<endl; <br> 
 bst.postorder(root); <br> 
 cout<<endl; <br> 
 break; <br> 
 case 6: <br> 
 cout<<"Display BST:"<<endl; <br> 
 bst.display(root,1); <br> 
 cout<<endl; <br> 
 break; <br> 
 case 7: <br> 
 exit(1); <br> 
 default: <br> 
 cout<<"Wrong choice"<<endl; v
 } <br> 
 } <br> 
} <br> <br> 
void BST::find(int item, node **par, node **loc) <br> <br> 
{ <br> 
 node *ptr, *ptrsave; <br> 
 if (root == NULL) <br> 
 { <br> 
 *loc = NULL; <br> 
 *par = NULL; <br> 
 return; <br> 
 } <br> 
 if (item == root->info) <br> 
 { <br> 
 *loc = root; <br> 
 *par = NULL; <br> 
 return; <br> 
 } <br> 
 if (item < root->info) <br> 
 ptr = root->left; <br> 
 else <br> 
 ptr = root->right; <br> 
 ptrsave = root; <br> 
 while (ptr != NULL) <br> 
 { <br> 
 if (item == ptr->info) <br> 
 { <br> 
 *loc = ptr; <br> 
 *par = ptrsave; <br> 
 return; <br> 
 } <br> 
 ptrsave = ptr; <br> 
 if (item < ptr->info) <br> 
 ptr = ptr->left; <br> 
 else <br> 
 ptr = ptr->right; <br> 
 } <br> 
 *loc = NULL; <br> 
 *par = ptrsave; <br> 
} <br> 

void BST::insert(node *tree, node *newnode) <br> 
{ <br> 
 if (root == NULL) <br> 
 { <br> 
 root = new node; <br> 
 root->info = newnode->info; <br> 
 root->left = NULL; <br> 
 root->right = NULL; <br> 
 cout<<"Root Node is Added"<<endl; <br> 
 return; <br> 
 } <br> 
 if (tree->info == newnode->info) <br> 
 { <br> 
 cout<<"Element already in the tree"<<endl; <br> 
 return; <br> 
 } <br> 
 if (tree->info > newnode->info) <br> 
 { <br> 
 if (tree->left != NULL) <br> 
 { <br> 
 insert(tree->left, newnode); <br> 
 } <br> 
 else <br> 
 { <br> 
 tree->left = newnode; <br> 
 (tree->left)->left = NULL; <br> 
 (tree->left)->right = NULL; <br> 
 cout<<"Node Added To Left"<<endl;<br>  
 return;<br>  
 } <br> 
 } <br> 
 else <br> 
 { <br> <br> 
 if (tree->right != NULL) <br> 
 { <br> 
 insert(tree->right, newnode); <br> 
 } <br> 
 else <br> 
 { <br> <br> 
 tree->right = newnode; <br> 
 (tree->right)->left = NULL; <br> 
 (tree->right)->right = NULL; <br> 
 cout<<"Node Added To Right"<<endl; <br> 
 return; <br> 
 } <br> 
 } <br> 
} <br> 
<br> 
void BST::del(int item) <br> 
{ <br> 
 node *parent, *location; <br> 
 if (root == NULL) <br> 
 { <br> 
 cout<<"Tree empty"<<endl; <br> 
 return; <br> 
 } <br> <br> 
 find(item, &parent, &location); <br> 
 if (location == NULL) <br> 
 { <br> <br> 
 cout<<"Item not present in tree"<<endl; <br> 
 return; <br> 
 } <br> 
 if (location->left == NULL && location->right == NULL) <br> 
 case_a(parent, location); <br> 
 if (location->left != NULL && location->right == NULL) <br> 
 case_b(parent, location); <br> 
 if (location->left == NULL && location->right != NULL) <br> 
 case_b(parent, location); <br> 
 if (location->left != NULL && location->right != NULL) <br> 
 case_c(parent, location); <br> 
 free(location); <br> 
} <br> 
 

void BST::case_a(node *par, node *loc ) <br> 
{ <br> <br> 
 if (par == NULL) <br> 
 { <br> 
 root = NULL; <br> 
 } <br> 
 else <br> 
 { <br> <br> 
 if (loc == par->left) <br> 
 par->left = NULL; <br> 
 else <br> 
 par->right = NULL; <br> 
 } <br> 
} <br> 
 

void BST::case_b(node *par, node *loc) <br> 
{ <br> 
 node *child; <br> 
 if (loc->left != NULL) <br> 
 child = loc->left; <br> 
 else <br> 
 child = loc->right; <br> 
 if (par == NULL) <br> 
 { <br> 
 root = child; <br> 
 } <br> 
 else <br> 
 { <br> 
 if (loc == par->left) <br> 
 par->left = child; <br> 
 else <br> 
 par->right = child; <br> 
 } <br> 
} <br> 
 

void BST::case_c(node *par, node *loc) <br> 
{ <br> 
 node *ptr, *ptrsave, *suc, *parsuc; <br> 
 ptrsave = loc; <br> 
 ptr = loc->right; <br> 
 while (ptr->left != NULL) <br> 
 { <br> <br> 
 ptrsave = ptr; <br> 
 ptr = ptr->left; <br> 
 } <br> 
 suc = ptr; <br> 
 parsuc = ptrsave; <br> 
 if (suc->left == NULL && suc->right == NULL) <br> 
 case_a(parsuc, suc); <br> 
 else <br> 
 case_b(parsuc, suc); <br> 
 if (par == NULL) <br> 
 { <br> 
 root = suc; 
 } <br> 
 else <br> 
 { <br> 
 if (loc == par->left) <br> 
 par->left = suc; <br> 
 else <br> 
 par->right = suc; <br> 
 } <br> 
 suc->left = loc->left; <br> 
 suc->right = loc->right; <br> 
} <br> 
 
 
void BST::preorder(node *ptr) <br> 
{ <br> 
 if (root == NULL) <br> 
 { <br> 
 cout<<"Tree is empty"<<endl; <br> 
 return; <br> 
 } <br> 
 if (ptr != NULL) <br> 
 { <br> 
 cout<<ptr->info<<" "; <br> 
 preorder(ptr->left); <br> 
 preorder(ptr->right); <br> 
 } <br> 
} <br> 

void BST::inorder(node *ptr) <br> 
{ <br> 
 if (root == NULL) <br> 
 { <br> 
 cout<<"Tree is empty"<<endl; <br> 
 return; <br> 
 } <br> 
 if (ptr != NULL) <br> 
 { <br> 
 inorder(ptr->left); <br> 
 cout<<ptr->info<<" "; <br> 
 inorder(ptr->right); <br> 
 } <br> 
} <br> 
 
void BST::postorder(node *ptr) <br> 
{ <br> 
 if (root == NULL) <br> 
 { <br> 
 cout<<"Tree is empty"<<endl; <br> 
 return; <br> 
 } <br> 
 if (ptr != NULL) <br> 
 { <br> 
 postorder(ptr->left); <br> 
 postorder(ptr->right); <br> 
 cout<<ptr->info<<" "; <br> 
 } <br> 
} 
 <br> 
void BST::display(node *ptr, int level) <br> 
{ <br> 
 int i; <br> 
 if (ptr != NULL) <br> 
 { <br> 
 display(ptr->right, level+1); <br> 
 cout<<endl; <br> 
 if (ptr == root) <br> 
 cout<<"Root->: "; <br> 
 else <br> 
 { <br> 
 for (i = 0;i < level;i++) <br> 
 cout<<" "; <br> 
 } <br> 
 cout<<ptr->info; <br> 
 display(ptr->left, level+1); <br> 
 } <br> 
}<br> 
Output:
*******<br>
![Screenshot (37)](https://user-images.githubusercontent.com/97940277/155927451-6f53476e-b378-4b19-b3d9-5236beba1726.png)<br>
![Screenshot (38)](https://user-images.githubusercontent.com/97940277/155927573-db445807-8abd-4edc-a3ff-80c06378e986.png)<br>
![Screenshot (39)](https://user-images.githubusercontent.com/97940277/155927666-97362262-0d36-4711-914c-14106f8faf9c.png)<br>
![Screenshot (40)](https://user-images.githubusercontent.com/97940277/155927787-a9e3fed8-5bd0-4be7-ae1a-f40d7d6b028d.png)<br>
![Screenshot (41)](https://user-images.githubusercontent.com/97940277/155927878-bcc5f824-975e-47e5-88c1-d9f3193e43ec.png)<br>
![Screenshot (44)](https://user-images.githubusercontent.com/97940277/155928085-9d0a9e80-556b-4e41-8b00-89e00974f9a9.png)<br>

	
*********************
6.C++ Program to Implement Min Heap<br>
*************
    #include<iostream><br> 
#include <conio.h><br>
using namespace std;<br>
void min_heap(int *a, int m, int n){<br>
   int j, t;<br>
   t= a[m];<br>
   j = 2 * m;<br>
   while (j <= n) {<br>
      if (j < n && a[j+1] < a[j])<br>
         j = j + 1;<br>
      if (t < a[j])<br>
         break;<br>
      else if (t >= a[j]) {<br>
         a[j/2] = a[j];<br>
         j = 2 * j;<br>
      }<br>
   }<br>
   a[j/2] = t;<br>
   return;<br>
}<br>
void build_minheap(int *a, int n) {<br>
   int k;<br>
   for(k = n/2; k >= 1; k--) {<br>
      min_heap(a,k,n);<br>
   }<br>
}<br>
int main() {<br>
   int n, i;<br>
   cout<<"enter no of elements of array\n";<br>
   cin>>n;<br>
   int a[30];<br>
   for (i = 1; i <= n; i++) {<br>
      cout<<"enter element"<<" "<<(i)<<endl;<br>
      cin>>a[i];<br>
   }<br>
   build_minheap(a, n);<br>
   cout<<"Min Heap\n";<br>
   for (i = 1; i <= n; i++) {<br>
      cout<<a[i]<<endl;<br>
   }<br>
   getch();<br>
}<br>
Output:<br>
**********<br>
![Screenshot (46)](https://user-images.githubusercontent.com/97940277/155932218-2ea0ab8f-b69c-4037-9ec8-dff7747d187f.png)<br>
	
******************
7..C++ Program to Implement Max Heap<br>
******************
#include <iostream><br>
using namespace std;<br>
void max_heap(int *a, int m, int n) {<br>
   int j, t;<br>
   t = a[m];<br>
   j = 2 * m;<br>
   while (j <= n) {<br>
      if (j < n && a[j+1] > a[j])<br>
         j = j + 1;<br>
      if (t > a[j])<br>
         break;<br>
      else if (t <= a[j]) {<br>
         a[j / 2] = a[j];<br>
         j = 2 * j;<br>
      }<br>
   }<br>
   a[j/2] = t;<br>
   return;<br>
}<br>
void build_maxheap(int *a,int n) {<br>
   int k;<br>
   for(k = n/2; k >= 1; k--) {<br>
      max_heap(a,k,n);<br>
   }<br>
}<br>
int main() {<br>
   int n, i;<br>
   cout<<"enter no of elements of array\n";<br>
   cin>>n;<br>
   int a[30];<br>
   for (i = 1; i <= n; i++) {<br>
      cout<<"enter elements"<<" "<<(i)<<endl;<br>
      cin>>a[i];<br>
   }<br>
   build_maxheap(a,n);<br>
   cout<<"Max Heap\n";<br>
   for (i = 1; i <= n; i++) {<br>
      cout<<a[i]<<endl;<br>
   }<br>
}	<br>

Output:<br>
**********<br>
![Screenshot (82)](https://user-images.githubusercontent.com/97940277/156970864-bde89a6d-7fe1-4159-af09-3ac0876648e5.png)<br>

********************
8. Program to implement heap sort.<br>
********************
 
  #include <iostream><br>
  using namespace std;<br>
  
  void heapify(int arr[], int n, int i) {<br>
    
      int largest = i;<br>
      int left = 2 * i + 1;<br>
      int right = 2 * i + 2;<br>
  
    if (left < n && arr[left] > arr[largest])<br>
      largest = left;<br>
  
    if (right < n && arr[right] > arr[largest])<br>
      largest = right;<br>

     if (largest != i) {<br>
      swap(arr[i], arr[largest]);<br>
      heapify(arr, n, largest);<br>
    }<br>
  }<br>
  
  void heapSort(int arr[], int n) {<br>
    for (int i = n / 2 - 1; i >= 0; i--)<br>
      heapify(arr, n, i);<br>

     for (int i = n - 1; i >= 0; i--) {<br>
      swap(arr[0], arr[i]);<br>
 
      
      heapify(arr, i, 0);<br>
    }<br>
  }<br>
  
  void printArray(int arr[], int n) {<br>
    for (int i = 0; i < n; ++i)<br>
    cout << arr[i] << " ";<br>
    cout << "\n";<br>
  }<br>
  

  int main() {<br>
    int arr[] = {1, 12, 9, 5, 6, 10};<br>
    int n = sizeof(arr) / sizeof(arr[0]);<br>
    heapSort(arr, n);<br>
  
    cout << "Sorted array is \n";<br>
    printArray(arr, n);<br>
  }<br>
Output:<br>
********<br>
 
 ![Screenshot (84)](https://user-images.githubusercontent.com/97940277/156971638-8950d4e2-b850-4066-9f38-6177608ead65.png)<br>

*************************************
9.Write a C++program to implement subset using backtracking</br>
*************************************
#include <iostream><br>
#include <stack><br>
 
using namespace std;<br>
 
int set[] = {10, 9, 5, 18, 12, 20, 15};
int numberOfElements = 7, sum = 32;
 
class SubSet{
public:
  stack<int> solutionSet;
  bool hasSolution;
  
  void solve(int s, int idx){
      
    //return if s exceed sum
    if(s>sum)
        return;
 
    //check if stack has the right subsets of numbers
    if(s==sum){
        hasSolution = true;
        //display stack contents
        displaySolutionSet();
        //Though found a solution but deliberately 
        //returning to find more
        return;
    }
        
 
    for(int i=idx; i<numberOfElements; i++){
        //Adding element to the stack
        solutionSet.push(set[i]);
 
        //add set[i] to the 's' and recusively start from next number
        solve(s+set[i],i+1);
        
        //Removing element from stack i.e Backtracking
        solutionSet.pop();
    }
  }
  
  //Function to display stack content
  void displaySolutionSet(){
        stack<int> temp;
      
        while (!solutionSet.empty()) 
        { 
            cout <<  solutionSet.top() << " "; 
            temp.push(solutionSet.top()); 
            solutionSet.pop();
        } 
        cout << '\n';
        while (!temp.empty()) 
        { 
            solutionSet.push(temp.top()); 
            temp.pop();
        } 
    }
};
 
int main()
{
    SubSet ss;
    ss.solve(0,0);
	    
	if(ss.hasSolution == false)
	    cout << "No Solution";
 
    return 0;
}	
Output:<br>
*********<br>
![Screenshot (86)](https://user-images.githubusercontent.com/97940277/157172838-e3b3b977-eb59-4c13-a8f0-453ab18b6873.png)<br>

******************
10.Implementing doubly linked list<br>
*****************
#include<iostream><br>
#include<cstdio><br>
#include<cstdlib>
using namespace std;<br>
struct node<br>
{<br><br>
    int info;<br><br>
    struct node *next;<br><br>
    struct node *prev;<br>
}*start;<br>
class double_llist<br>
{<br>
    public:<br>
        void create_list(int value);<br>
        void add_begin(int value);<br>
        void add_after(int value, int position);<br>
        void delete_element(int value);<br>
        void search_element(int value);<br>
        void display_dlist();<br>
        void count();<br><br>
        void reverse();<br>
        double_llist()<br>
        {<br>
            start = NULL;  <br><br>
        }<br>
};<br>
 int main()<br>
{<br>
    int choice, element, position;<br>
    double_llist dl;<br>
    while (1)<br>
    {<br>
        cout<<endl<<"----------------------------"<<endl;<br>
        cout<<endl<<"Operations on Doubly linked list"<<endl;<br>
        cout<<endl<<"----------------------------"<<endl;    <br>    
        cout<<"1.Create Node"<<endl;<br>
        cout<<"2.Add at begining"<<endl;<br>
        cout<<"3.Add after position"<<endl;<br>
        cout<<"4.Delete"<<endl;<br>
        cout<<"5.Display"<<endl;
        cout<<"6.Count"<<endl;<br>
        cout<<"7.Reverse"<<endl;<br>
        cout<<"8.Quit"<<endl;<br>
        cout<<"Enter your choice : ";<br>
        cin>>choice;<br>
        switch ( choice )<br>
        {<br>
        case 1:<br>
            cout<<"Enter the element: ";<br>
            cin>>element;<br>
            dl.create_list(element);<br><br>
            cout<<endl;<br>
            break;<br>
        case 2:<br>
            cout<<"Enter the element: ";<br>
            cin>>element;
            dl.add_begin(element);<br>
            cout<<endl;<br>
            break;<br>
        case 3:<br>
            cout<<"Enter the element: ";<br>
            cin>>element;<br>
            cout<<"Insert Element after postion: ";<br>
            cin>>position;<br>
            dl.add_after(element, position);<br>
            cout<<endl;<br>
            break;<br>
        case 4:<br>
            if (start == NULL)<br>
            {         <br>             
                cout<<"List empty,nothing to delete"<<endl;  <br>
                break;<br><br><br><br><br><br>
            }<br><br><br><br><br><br>
            cout<<"Enter the element for deletion: ";<br><br><br><br><br><br>
            cin>>element;<br><br><br><br><br><br>
            dl.delete_element(element);<br><br><br><br><br><br>
            cout<<endl;<br><br><br><br><br><br>
            break;<br><br><br><br><br><br>
        case 5:<br><br><br><br><br><br>
            dl.display_dlist();<br><br><br><br><br><br>
            cout<<endl;<br><br><br><br><br>
            break;<br><br><br><br><br>
        case 6:<br><br><br><br><br>
            dl.count();<br><br><br><br><br>
            break;  <br><br><br><br><br>  
        case 7:<br><br><br><br><br>
            if (start == NULL)<br><br><br><br><br>
            {<br><br><br><br><br>
                cout<<"List empty,nothing to reverse"<<endl;<br><br><br><br><br>
                break;<br><br><br><br><br>
            }<br><br><br><br><br>
            dl.reverse();<br><br><br><br>
            cout<<endl;<br><br><br><br>
            break;<br><br><br><br>
        case 8:<br><br><br><br>
            exit(1);<br><br><br><br>
        default:<br><br><br><br>
            cout<<"Wrong choice"<<endl;<br><br><br><br>
        }<br><br><br><br>
    }<br><br><br><br>
    return 0;<br><br><br><br>
}<br><br><br><br>
 void double_llist::create_list(int value)<br><br><br><br>
{<br><br><br>
    struct node *s, *temp;<br><br><br>
    temp = new(struct node);<br><br><br>
    temp->info = value;<br><br><br>
    temp->next = NULL;<br><br><br>
    if (start == NULL)<br><br><br>
    {<br><br><br>
        temp->prev = NULL;<br><br><br>
        start = temp;<br><br><br>
    }<br><br><br>
    else<br><br><br>
    {<br><br><br>
        s = start;<br><br><br>
        while (s->next != NULL)<br><br><br>
            s = s->next;<br><br><br>
        s->next = temp;<br><br><br>
        temp->prev = s;<br><br><br>
    }<br><br>
}<br><br>
 void double_llist::add_begin(int value)<br><br>
{
    if (start == NULL)<br><br>
    {<br><br>
        cout<<"First Create the list."<<endl;<br><br>
        return;<br><br>
    }<br><br>
    struct node *temp;
    temp = new(struct node);<br><br>
    temp->prev = NULL;<br><br>
    temp->info = value;<br><br>
    temp->next = start;<br><br>
    start->prev = temp;<br><br>
    start = temp;<br><br>
    cout<<"Element Inserted"<<endl;<br>
}<br>
void double_llist::add_after(int value, int pos)<br>
{<br>
    if (start == NULL)<br>
    {<br>
        cout<<"First Create the list."<<endl;<br>
        return;<br>
    }<br>
    struct node *tmp, *q;<br>
    int i;<br>
    q = start;<br>
    for (i = 0;i < pos - 1;i++)<br>
    {<br>
        q = q->next;
        if (q == NULL)<br>
        {<br>
            cout<<"There are less than ";<br>
            cout<<pos<<" elements."<<endl;<br>
            return;<br>
        }
    }<br>
    tmp = new(struct node);<br>
    tmp->info = value;<br>
    if (q->next == NULL)<br>
    {
        q->next = tmp;<br>
        tmp->next = NULL;<br>
        tmp->prev = q;   <br>  <br> 
    }<br>
    else<br>
    {<br>
        tmp->next = q->next;<br>
        tmp->next->prev = tmp;<br>
        q->next = tmp;<br>
        tmp->prev = q;<br>
    }<br>
    cout<<"Element Inserted"<<endl;<br>
}<br>
 void double_llist::delete_element(int value)<br>
{<br>
    struct node *tmp, *q;<br>
        if (start->info == value)<br>
    {<BR><br>
        tmp = start;
        start = start->next;<br>  
        start->prev = NULL;<br>
        cout<<"Element Deleted"<<endl;<br>
        free(tmp);<br>
        return;<br>
    }<br>
    q = start;<br>
    while (q->next->next != NULL)<br>
    { <br>
               if (q->next->info == value)  <br><br><br>
        {<br>
            tmp = q->next;<br>
            q->next = tmp->next;<br>
            tmp->next->prev = q;<br>
            cout<<"Element Deleted"<<endl;<br>
            free(tmp);<br>
            return;<br><br>
        }<br><br>
        q = q->next;<br><br>
    }<br><br>
        if (q->next->info == value)    <br><br>
    {<br><br>
        tmp = q->next;<br><br>
        free(tmp);<br><br>
        q->next = NULL;<br><br>
        cout<<"Element Deleted"<<endl;<br><br>
        return;<br><br>
    }<br><br>
    cout<<"Element "<<value<<" not found"<<endl;<br><br>
}<br><br>
 void double_llist::display_dlist()<br><br>
{<br><br>
    struct node *q;<br><br>
    if (start == NULL)<br><br>
    {<br><br>
        cout<<"List empty,nothing to display"<<endl;<br><br>
        return;<br><br>
    }<br>
    q = start;<br>
    cout<<"The Doubly Link List is :"<<endl;<br>
    while (q != NULL)<br>
    {
        cout<<q->info<<" <-> ";<br>
        q = q->next;<br>
    }<br>
    cout<<"NULL"<<endl;<br>
}<br>
 void double_llist::count()<br>
{<br>
    struct node *q = start;<br>
    int cnt = 0;<br>
    while (q != NULL)<br><br>
    {<br>
        q = q->next;<br>
        cnt++;<br>
    }
    cout<<"Number of elements are: "<<cnt<<endl;<br>
}<br>
 void double_llist::reverse()<br>
{<br>
    struct node *p1, *p2;<br>
    p1 = start;<br>
    p2 = p1->next;<br>
    p1->next = NULL;<br>
    p1->prev = p2;<br>
    while (p2 != NULL)<br>
    {
        p2->prev = p2->next;<br>
        p2->next = p1;<br>
        p1 = p2;<br>
        p2 = p2->prev;<br>
    }<br>
    start = p1;<br>
    cout<<"List Reversed"<<endl;<br>
}

Output:<br>
********<br>
![Screenshot (160)](https://user-images.githubusercontent.com/97940277/163759755-d480a09a-6349-4aa1-9a7e-88dcffa0b61a.png)<br>
![Screenshot (161)](https://user-images.githubusercontent.com/97940277/163759850-0e2bc72a-8bc7-499a-8e3e-c40872911f17.png)<br>
![Screenshot (162)](https://user-images.githubusercontent.com/97940277/163759985-d8292c39-af25-4e8d-9b78-811cdd0be704.png)<br>
![Screenshot (163)](https://user-images.githubusercontent.com/97940277/163760147-17cbb7ea-0b46-454c-be91-07948b092695.png)<br>
![Screenshot (164)](https://user-images.githubusercontent.com/97940277/163760339-47f0b9b5-a149-4176-ac24-a2708e2b272b.png)<br>

10) 
#include<iostream>
using namespace std;
struct node
{
   int key;
   node *parent;
   char color;
   node *left;
   node *right;
};
class RBtree
 {
  node *root;
  node *q;
 public :
  RBtree()
  {
          q=NULL;
          root=NULL;
  }
  void insert();
  void insertfix(node *);
  void leftrotate(node *);
  void rightrotate(node *);
  void del();
  node* successor(node *);
  void delfix(node *);
  void disp();
  void display( node *);
 // void search();
};
void RBtree::insert()
 {
 int z,i=0;
 cout<<"\nEnter key of the node to be inserted: "; cin>>z;
 node *p,*q;
 node *t=new node;
 t->key=z;
 t->left=NULL;
 t->right=NULL;
 t->color='r';
 p=root;
 q=NULL;
 if(root==NULL)
 {
       root=t;
       t->parent=NULL;
 }
 else
 {
     while(p!=NULL)
     {
          q=p;
          if(p->key<t->key)
              p=p->right;
          else
              p=p->left;
     }
     t->parent=q;
     if(q->key<t->key)
          q->right=t;
     else
          q->left=t;
 }
 insertfix(t);
}
void RBtree::insertfix(node *t)
 {
 node *u;
 if(root==t)
 {
     t->color='b';
     return;
 }
 while(t->parent!=NULL&&t->parent->color=='r')
 {
       node *g=t->parent->parent;
       if(g->left==t->parent)
       {
                    if(g->right!=NULL)
                    {
                          u=g->right;
                          if(u->color=='r')
                          {
                               t->parent->color='b';
                               u->color='b';
                               g->color='r';
                               t=g;
                          }
                    }
                    else
                    {
                        if(t->parent->right==t)
                        {
                             t=t->parent;
                             leftrotate(t);
                        }
                        t->parent->color='b';
                        g->color='r';
                        rightrotate(g);
                    }
       }
       else
       {
                    if(g->left!=NULL)
                    {
                         u=g->left;
                         if(u->color=='r')
                         {
                              t->parent->color='b';
                              u->color='b';
                              g->color='r';
                              t=g;
                         }
                    }
                    else
                    {
                        if(t->parent->left==t)
                        {
                               t=t->parent;
                               rightrotate(t);
                        }
                        t->parent->color='b';
                        g->color='r';
                        leftrotate(g);
                    }
       }
       root->color='b';
 }
}
void RBtree::del()
{
 if(root==NULL)
 {
       cout<<"\nEmpty Tree." ;
       return ;
 }
 int x;
 cout<<"\nEnter the key of the node to be deleted: "; cin>>x;
 node *p;
 p=root;
 node *y=NULL;
 node *q=NULL;
 int found=0;
 while(p!=NULL&&found==0)
 {
       if(p->key==x)
           found=1;
       if(found==0)
       {
             if(p->key<x) p=p->right;
             else
                p=p->left;
       }
 }
 if(found==0)
 {
        cout<<"\nElement Not Found.";
        return ;
 }
 else
 {
     cout<<"\nDeleted Element: "<<p->key;
     cout<<"\nColour: "; if(p->color=='b')
 cout<<"Black\n";
else
 cout<<"Red\n"; if(p->parent!=NULL)
           cout<<"\nParent: "<<p->parent->key;
     else
           cout<<"\nThere is no parent of the node. "; if(p->right!=NULL)
           cout<<"\nRight Child: "<<p->right->key;
     else
           cout<<"\nThere is no right child of the node. "; if(p->left!=NULL)
           cout<<"\nLeft Child: "<<p->left->key;
     else
           cout<<"\nThere is no left child of the node.  ";
     cout<<"\nNode Deleted."; if(p->left==NULL||p->right==NULL)
          y=p;
     else
          y=successor(p);
     if(y->left!=NULL)
          q=y->left;
     else
     {
          if(y->right!=NULL)
               q=y->right;
          else
               q=NULL;
     }
     if(q!=NULL)
          q->parent=y->parent;
     if(y->parent==NULL)
          root=q;
     else
     {
         if(y==y->parent->left)
            y->parent->left=q;
         else
            y->parent->right=q;
     }
     if(y!=p)
     {
         p->color=y->color;
         p->key=y->key;
     }
     if(y->color=='b')
         delfix(q);
 }
}
void RBtree::delfix(node *p)
{
node *s;
while(p!=root&&p->color=='b')
{
      if(p->parent->left==p)
      {
              s=p->parent->right;
              if(s->color=='r')
              {
                     s->color='b';
                     p->parent->color='r';
                     leftrotate(p->parent);
                     s=p->parent->right;
              }
              if(s->right->color=='b'&&s->left->color=='b')
              {
                     s->color='r';
                     p=p->parent;
              }
              else
              {
                  if(s->right->color=='b')
                  {
                         s->left->color=='b';
                         s->color='r';
                         rightrotate(s);
                         s=p->parent->right;
                  }
                  s->color=p->parent->color;
                  p->parent->color='b';
                  s->right->color='b';
                  leftrotate(p->parent);
                  p=root;
              }
      }
      else
      {
              s=p->parent->left;
              if(s->color=='r')
              {
                    s->color='b';
                    p->parent->color='r';
                    rightrotate(p->parent);
                    s=p->parent->left;
              }
              if(s->left->color=='b'&&s->right->color=='b')
              {
                    s->color='r';
                    p=p->parent;
              }
              else
              {
                    if(s->left->color=='b')
                    {
                          s->right->color='b';
                          s->color='r';
                          leftrotate(s);
                          s=p->parent->left;
                    }
                    s->color=p->parent->color;
                    p->parent->color='b';
                    s->left->color='b';
                    rightrotate(p->parent);
                    p=root;
              }
      }
   p->color='b';
   root->color='b';
}
}
void RBtree::leftrotate(node *p)
{
 if(p->right==NULL)
       return ;
 else
 {
       node *y=p->right;
       if(y->left!=NULL)
       {
              p->right=y->left;
              y->left->parent=p;
       }
       else
              p->right=NULL;
       if(p->parent!=NULL)
            y->parent=p->parent;
       if(p->parent==NULL)
            root=y;
       else
       {
           if(p==p->parent->left)
                   p->parent->left=y;
           else
                   p->parent->right=y;
       }
       y->left=p;
       p->parent=y;
 }
}
void RBtree::rightrotate(node *p)
 {
 if(p->left==NULL)
      return ;
 else
 {
     node *y=p->left;
     if(y->right!=NULL)
     {
              p->left=y->right;
              y->right->parent=p;
     }
     else
             p->left=NULL;
     if(p->parent!=NULL)
             y->parent=p->parent;
     if(p->parent==NULL)
           root=y;
     else
     {
         if(p==p->parent->left)
               p->parent->left=y;
         else
               p->parent->right=y;
     }
     y->right=p;
     p->parent=y;
 }
}
node* RBtree::successor(node *p)
{
  node *y=NULL;
 if(p->left!=NULL)
 {
     y=p->left;
     while(y->right!=NULL)
          y=y->right;
 }
 else
 {
     y=p->right;
     while(y->left!=NULL)
          y=y->left;
 }
 return y;
}
void RBtree::disp()
{
 display(root);
}
void RBtree::display(node *p)
 {
 if(root==NULL)
 {
      cout<<"\nEmpty Tree.";
      return ;
 }
 if(p!=NULL)
 {
            cout<<"\n\t NODE: ";
            cout<<"\n Key: "<<p->key;
            cout<<"\n Colour: "; if(p->color=='b')
 cout<<"Black";
else
 cout<<"Red"; if(p->parent!=NULL)
                   cout<<"\n Parent: "<<p->parent->key;
            else
                   cout<<"\n There is no parent of the node. "; if(p->right!=NULL)
                   cout<<"\n Right Child: "<<p->right->key;
            else
                   cout<<"\n There is no right child of the node. "; if(p->left!=NULL)
                   cout<<"\n Left Child: "<<p->left->key;
            else
                   cout<<"\n There is no left child of the node.  ";
            cout<<endl; if(p->left)
{
             cout<<"\n\nLeft:\n"; display(p->left);
}
/*else
 cout<<"\nNo Left Child.\n";*/ if(p->right)
{
 cout<<"\n\nRight:\n"; display(p->right);
}
/*else
 cout<<"\nNo Right Child.\n"*/
 }
}
void RBtree::search()
 {
 if(root==NULL)
 {
       cout<<"\nEmpty Tree\n" ;
       return  ;
 }
 int x;
 cout<<"\n Enter key of the node to be searched: "; cin>>x;
 node *p=root;
 int found=0;
 while(p!=NULL&& found==0)
 {
        if(p->key==x)
            found=1;
        if(found==0)
        {
             if(p->key<x) p=p->right;
             else
                  p=p->left;
        }
 }
 if(found==0)
      cout<<"\nElement Not Found.";
 else
 {
            cout<<"\n\t FOUND NODE: ";
            cout<<"\n Key: "<<p->key;
            cout<<"\n Colour: "; if(p->color=='b')
 cout<<"Black";
else
 cout<<"Red"; if(p->parent!=NULL)
                   cout<<"\n Parent: "<<p->parent->key;
            else
                   cout<<"\n There is no parent of the node. "; if(p->right!=NULL)
                   cout<<"\n Right Child: "<<p->right->key;
            else
                   cout<<"\n There is no right child of the node. "; if(p->left!=NULL)
                   cout<<"\n Left Child: "<<p->left->key;
            else
                   cout<<"\n There is no left child of the node.  ";
            cout<<endl;
 }
 }
 int main()
 {
int ch,y=0;
RBtree obj;
do
{
            cout<<"\n\t RED BLACK TREE " ;
            cout<<"\n 1. Insert in the tree ";
            cout<<"\n 2. Delete a node from the tree";
            cout<<"\n 3. Search for an element in the tree";
            cout<<"\n 3. Display the tree ";
            cout<<"\n 4. Exit " ;
            cout<<"\nEnter Your Choice: "; cin>>ch;
            switch(ch)
            {
                      case 1 : obj.insert();
                               cout<<"\nNode Inserted.\n";
                               break;
                      case 2 : obj.del();
                               break;
                      case 3 : obj.search();
                              // break;
                      case 4 : obj.disp();
                               break;
                      case 5 : y=1;
                               break;
                      default : cout<<"\nEnter a Valid Choice.";
            }
            cout<<endl;
}while(y!=1);
return 1;
}



Doubly linked list
 #include<iostream>
#include<cstdio>
#include<cstdlib>
/*
* Node Declaration
*/
using namespace std;
struct node
{
int info;
struct node *next;
struct node *prev;
}*start;

/*
Class Declaration 
*/
class double_llist
{
public:
    void create_list(int value);
    void add_begin(int value);
    void add_after(int value, int position);
    void delete_element(int value);
    void display_dlist();
    double_llist()
    {
        start = NULL;  
    }
};

/*
* Main: Conatins Menu
*/
int main()
 {
int choice, element, position;
double_llist dl;
while (1)
{
    cout<<endl<<"----------------------------"<<endl;
    cout<<endl<<"Operations on Doubly linked list"<<endl;
    cout<<endl<<"----------------------------"<<endl;         
    cout<<"1.Create Node"<<endl;
    cout<<"2.Add at begining"<<endl;
    cout<<"3.Add after position"<<endl;
    cout<<"4.Delete"<<endl;
    cout<<"5.Display"<<endl;
    cout<<"6.Quit"<<endl;
    cout<<"Enter your choice : ";
    cin>>choice;
    switch ( choice )
    {
    case 1:
        cout<<"Enter the element: ";
        cin>>element;
        dl.create_list(element);
        cout<<endl;
        break;
    case 2:
        cout<<"Enter the element: ";
        cin>>element;
        dl.add_begin(element);
        cout<<endl;
        break;
    case 3:
        cout<<"Enter the element: ";
        cin>>element;
        cout<<"Insert Element after postion: ";
        cin>>position;
        dl.add_after(element, position);
        cout<<endl;
        break;
    case 4:
        if (start == NULL)
        {                      
            cout<<"List empty,nothing to delete"<<endl;   
            break;
        }
        cout<<"Enter the element for deletion: ";
        cin>>element;
        dl.delete_element(element);
        cout<<endl;
        break;
    case 5:
        dl.display_dlist();
        cout<<endl;
        break;
    case 6:
        exit(1);
    default:
        cout<<"Wrong choice"<<endl;
    }
}
return 0;
}

/*
 * Create Double Link List
*/
void double_llist::create_list(int value)
 {
struct node *s, *temp;
temp = new(struct node); 
temp->info = value;
temp->next = NULL;
if (start == NULL)
{
    temp->prev = NULL;
    start = temp;
}
else
{
    s = start;
    while (s->next != NULL)
        s = s->next;
    s->next = temp;
    temp->prev = s;
}
}

/*
 * Insertion at the beginning
 */
void double_llist::add_begin(int value)
 {
if (start == NULL)
{
    cout<<"First Create the list."<<endl;
    return;
}
struct node *temp;
temp = new(struct node);
temp->prev = NULL;
temp->info = value;
temp->next = start;
start->prev = temp;
start = temp;
cout<<"Element Inserted"<<endl;
 }

 /*
 * Insertion of element at a particular position
 */
 void double_llist::add_after(int value, int pos)
 {
if (start == NULL)
{
    cout<<"First Create the list."<<endl;
    return;
}
struct node *tmp, *q;
int i;
q = start;
for (i = 0;i < pos - 1;i++)
{
    q = q->next;
    if (q == NULL)
    {
        cout<<"There are less than ";
        cout<<pos<<" elements."<<endl;
        return;
    }
}
tmp = new(struct node);
tmp->info = value;
if (q->next == NULL)
{
    q->next = tmp;
    tmp->next = NULL;
    tmp->prev = q;      
}
else
{
    tmp->next = q->next;
    tmp->next->prev = tmp;
    q->next = tmp;
    tmp->prev = q;
}
cout<<"Element Inserted"<<endl;
}

/*
 * Deletion of element from the list
*/
void double_llist::delete_element(int value)
{
struct node *tmp, *q;
 /*first element deletion*/
if (start->info == value)
{
    tmp = start;
    start = start->next;  
    start->prev = NULL;
    cout<<"Element Deleted"<<endl;
    free(tmp);
    return;
}
q = start;
while (q->next->next != NULL)
{   
    /*Element deleted in between*/
    if (q->next->info == value)  
    {
        tmp = q->next;
        q->next = tmp->next;
        tmp->next->prev = q;
        cout<<"Element Deleted"<<endl;
        free(tmp);
        return;
    }
    q = q->next;
}
 /*last element deleted*/
if (q->next->info == value)    
{ 	
    tmp = q->next;
    free(tmp);
    q->next = NULL;
    cout<<"Element Deleted"<<endl;
    return;
}
cout<<"Element "<<value<<" not found"<<endl;
}

/*
 * Display elements of Doubly Link List
*/
void double_llist::display_dlist()
 {
struct node *q;
if (start == NULL)
{
    cout<<"List empty,nothing to display"<<endl;
    return;
}
q = start;
cout<<"The Doubly Link List is :"<<endl;
while (q != NULL)
{
    cout<<q->info<<" <-> ";
    q = q->next;
}
cout<<"NULL"<<endl;
 }

/*
* Number of elements in Doubly Link List

 void double_llist::count()
 { 	
struct node *q = start;
int cnt = 0;
while (q != NULL)
{
    q = q->next;
    cnt++;
}
cout<<"Number of elements are: "<<cnt<<endl;
}


 * Reverse Doubly Link List

void double_llist::reverse()
{
struct node *p1, *p2;
p1 = start;
p2 = p1->next;
p1->next = NULL;
p1->prev = p2;
while (p2 != NULL)
{
    p2->prev = p2->next;
    p2->next = p1;
    p1 = p2;
    p2 = p2->prev; 
}
start = p1;
cout<<"List Reversed"<<endl; 
}*/
	













Ghj

