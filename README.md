# Reverse-Linked-List


#include<stdio.h>
#include<stdlib.h>

struct Node{
	int data;
	struct Node* link;
	
};

void reverse(struct Node **head)
{

	struct Node*prev =NULL;
	struct Node*current= *head;
	struct Node*next;
	
	while(current!=NULL)
	{
		next= current->link;
		current->link=prev;
		prev=current;
		current=next;
    
	}
	
	*head=prev;
}


void insert(struct Node **head, int data)
{

	struct Node *p=malloc(sizeof(struct Node));
	p->data=data;
	p->link=*head;
	*head=p;
  
}

void display(struct Node *head)
{

	struct Node*temp=head;
	while(temp!=NULL)
	{
  
		printf("%d\t",temp->data);
		temp=temp->link;
    
	}
	printf("\n");
}

int main()
{

	struct Node*head=NULL;
	
	insert(&head,10);
	insert(&head,15);
	insert(&head,18);
	insert(&head,133);
	
	printf("given linked list\n");
	display(head);
		
	reverse(&head);	
	printf("reversed linked list\n");
	display(head);
	
	return 0;
	
}
