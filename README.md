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
9.
	














