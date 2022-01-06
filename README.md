# operation-on-two-list-concatination-
#include<stdio.h>
#include<stdlib.h>
struct sll
{
int data;
struct sll *next;
};
typedef struct sll node;
node *addnode(node *,node *);
node *create(node *first)
{
node *new,*prev;
int x;
printf("enter data(enter -1 to stop)");
scanf("%d",&x);
while(x!=-1)
{
new=(node *)malloc(sizeof(node));
new->data=x;
new->next=NULL;
if(first==NULL)
{
first=new;
prev=new;
}
else
{
prev->next=new;
prev=new;
}
printf("enter data(enter -1 to stop)");
scanf("%d",&x);
}
return first;
}
void display(node *first)
{
node *temp=first;
if(first==NULL)
{
printf("no list to print");
}
else
{
while(temp!=NULL)
{
printf("|%d|->",temp->data);
temp=temp->next;
}
printf("NULL");
}
}
node *listsunion(node *l1,node *l2)
{
node *new,*l3=NULL;
while(l1!=NULL && l2!=NULL)
{
new=(node *)malloc(sizeof(node));
if(l1->data<l2->data)
{
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
}
else if(l2->data<l1->data)
{
new->data=l2->data;
new->next=NULL;
l3=addnode(l3,new);
l2=l2->next;
}
else
{
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
l2=l2->next;
}
}
if(l1==NULL)
{
while(l2!=NULL)
{
new=(node *)malloc(sizeof(node));
new->data=l2->data;
new->next=NULL;
l3=addnode(l3,new);
l2=l2->next;
}
}
if(l2==NULL)
{
while(l1!=NULL)
{
new=(node *)malloc(sizeof(node));
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
}
}
return l3;
}
node *intersection(node *l1,node *l2)
{
node *l3=NULL,*new;
while(l1!=NULL && l2!=NULL)
{
if(l1->data<l2->data)
{
l1=l1->next;
}
else if(l2->data<l1->data)
{
l2=l2->next;
}
else
{
new=(node *)malloc(sizeof(node));
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
l2=l2->next;
}
}
return l3;
}
node *merge(node *l1,node *l2)
{
node *new,*l3=NULL,*prev;
while(l1!=NULL&&l2!=NULL)
{
new=(node *)malloc(sizeof(node));
prev=(node *)malloc(sizeof(node));
if(l1->data==l2->data)
{
new->data=l1->data;
new->next=NULL;
prev->data=l2->data;
prev->next=NULL;
l3=addnode(l3,new);
l3=addnode(l3,prev);
l1=l1->next;
l2=l2->next;
}
else if(l1->data<l2->data)
{
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
}
else
{
new->data=l2->data;
new->next=NULL;
l3=addnode(l3,new);
l2=l2->next;
}
}

if(l1==NULL)
{
while(l2!=NULL)
{
new=(node *)malloc(sizeof(node));
new->data=l2->data;
new->next=NULL;
l3=addnode(l3,new);
l2=l2->next;
}
}
if(l2==NULL)
{
while(l1!=NULL)
{
new=(node *)malloc(sizeof(node));
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
}
}
return l3;
}
node *concatenate(node *l1,node *l2)
{
node *temp;
if(l1==NULL)
return l2;
else if(l2==NULL)
return l1;
else
{
temp=l1;
while(temp->next!=NULL)
{
temp=temp->next;
}
temp->next=l2;
}
return l1;
}
node *addnode(node *l3,node *new)
{
node *temp;
if(l3==NULL)
{
l3=new;
}
else
{
temp=l3;
while(temp->next!=NULL)
{
temp=temp->next;
}
temp->next=new;
}
return l3;
}
int main()
{
node *head=NULL,*l1,*l2;
int ch;
l1=create(head);
printf("enter second list\n");
l2=create(head);
printf("1:union\n 2:intersection\n 3:merge\n 4:concatenate 5:exit\n");
while(1)
{
printf("enter choice\n");
scanf("%d",&ch);
switch(ch)
{
case 4:head=concatenate(l1,l2);
display(head);
 break;
case 1:head=listsunion(l1,l2);
 display(head);
 break;
case 2:head=intersection(l1,l2);
 display(head);
 break;
case 3:head=merge(l1,l2);
 display(head);
 break;
case 5:exit(0);
 break;
default:printf("check choice");
}
}
}
  #include<stdio.h>
#include<stdlib.h>
struct sll
{
int data;
struct sll *next;
};
typedef struct sll node;
node *addnode(node *,node *);
node *create(node *first)
{
node *new,*prev;
int x;
printf("enter data(enter -1 to stop)");
scanf("%d",&x);
while(x!=-1)
{
new=(node *)malloc(sizeof(node));
new->data=x;
new->next=NULL;
if(first==NULL)
{
first=new;
prev=new;
}
else
{
prev->next=new;
prev=new;
}
printf("enter data(enter -1 to stop)");
scanf("%d",&x);
}
return first;
}
void display(node *first)
{
node *temp=first;
if(first==NULL)
{
printf("no list to print");
}
else
{
while(temp!=NULL)
{
printf("|%d|->",temp->data);
temp=temp->next;
}
printf("NULL");
}
}
node *listsunion(node *l1,node *l2)
{
node *new,*l3=NULL;
while(l1!=NULL && l2!=NULL)
{
new=(node *)malloc(sizeof(node));
if(l1->data<l2->data)
{
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
}
else if(l2->data<l1->data)
{
new->data=l2->data;
new->next=NULL;
l3=addnode(l3,new);
l2=l2->next;
}
else
{
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
l2=l2->next;
}
}
if(l1==NULL)
{
while(l2!=NULL)
{
new=(node *)malloc(sizeof(node));
new->data=l2->data;
new->next=NULL;
l3=addnode(l3,new);
l2=l2->next;
}
}
if(l2==NULL)
{
while(l1!=NULL)
{
new=(node *)malloc(sizeof(node));
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
}
}
return l3;
}
node *intersection(node *l1,node *l2)
{
node *l3=NULL,*new;
while(l1!=NULL && l2!=NULL)
{
if(l1->data<l2->data)
{
l1=l1->next;
}
else if(l2->data<l1->data)
{
l2=l2->next;
}
else
{
new=(node *)malloc(sizeof(node));
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
l2=l2->next;
}
}
return l3;
}
node *merge(node *l1,node *l2)
{
node *new,*l3=NULL,*prev;
while(l1!=NULL&&l2!=NULL)
{
new=(node *)malloc(sizeof(node));
prev=(node *)malloc(sizeof(node));
if(l1->data==l2->data)
{
new->data=l1->data;
new->next=NULL;
prev->data=l2->data;
prev->next=NULL;
l3=addnode(l3,new);
l3=addnode(l3,prev);
l1=l1->next;
l2=l2->next;
}
else if(l1->data<l2->data)
{
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
}
else
{
new->data=l2->data;
new->next=NULL;
l3=addnode(l3,new);
l2=l2->next;
}
}

if(l1==NULL)
{
while(l2!=NULL)
{
new=(node *)malloc(sizeof(node));
new->data=l2->data;
new->next=NULL;
l3=addnode(l3,new);
l2=l2->next;
}
}
if(l2==NULL)
{
while(l1!=NULL)
{
new=(node *)malloc(sizeof(node));
new->data=l1->data;
new->next=NULL;
l3=addnode(l3,new);
l1=l1->next;
}
}
return l3;
}
node *concatenate(node *l1,node *l2)
{
node *temp;
if(l1==NULL)
return l2;
else if(l2==NULL)
return l1;
else
{
temp=l1;
while(temp->next!=NULL)
{
temp=temp->next;
}
temp->next=l2;
}
return l1;
}
node *addnode(node *l3,node *new)
{
node *temp;
if(l3==NULL)
{
l3=new;
}
else
{
temp=l3;
while(temp->next!=NULL)
{
temp=temp->next;
}
temp->next=new;
}
return l3;
}
int main()
{
node *head=NULL,*l1,*l2;
int ch;
l1=create(head);
printf("enter second list\n");
l2=create(head);
printf("1:union\n 2:intersection\n 3:merge\n 4:concatenate 5:exit\n");
while(1)
{
printf("enter choice\n");
scanf("%d",&ch);
switch(ch)
{
case 4:head=concatenate(l1,l2);
display(head);
 break;
case 1:head=listsunion(l1,l2);
 display(head);
 break;
case 2:head=intersection(l1,l2);
 display(head);
 break;
case 3:head=merge(l1,l2);
 display(head);
 break;
case 5:exit(0);
 break;
default:printf("check choice");
}
}
}
  enter data(enter -1 to stop)90
enter data(enter -1 to stop)80
enter data(enter -1 to stop)50
enter data(enter -1 to stop)-1
enter second list
enter data(enter -1 to stop)51
enter data(enter -1 to stop)52
enter data(enter -1 to stop)96
enter data(enter -1 to stop)-1
1:union
 2:intersection
 3:merge
 4:concatenate 5:exit
enter choice
1
|51|->|52|->|90|->|80|->|50|->|96|->NULLenter choice
2
no list to printenter choice
3
|51|->|52|->|90|->|80|->|50|->|96|->NULLenter choice
4
|90|->|80|->|50|->|51|->|52|->|96|->NULLenter choice
5
