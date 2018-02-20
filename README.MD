#include<stdio.h>

struct node
{
    int data;
    struct node *next;
}*p;

void main()
{
   int choice,n;

   while(1)
   {
       printf("\nMainMenu: ");
       printf("\n1. Inserting at beginning");
       printf("\n2. Inserting at end");
       printf("\n3. Inserting after given node");
       printf("\n4. Deleting at beginning");
       printf("\n5. Deleting at end");
       printf("\n6. Deleting of given node");
       printf("\n7. Display List");
       printf("\n8. Count number of nodes in list");
       printf("\n9. Search List");

       printf("\nEnter your choice: ");
       scanf("%d", &choice);

       switch(choice)
       {
        case 1:
            printf("Enter value to be inserted: ");
            scanf("%d", &n);
            addatb(n);
            break;
        case 2:
            printf("Enter value to be inserted: ");
            scanf("%d", &n);
            addate(n);
            break;
        case 3:
            printf("Enter value to be inserted: ");
            scanf("%d", &n);
            addatg(n);
            break;
        case 4:
            delatb(n);
            break;
        case 5:
            delate(n);
            break;
        case 6:
            delofg(n);
            break;
        case 7:
            display();
            break;
        case 8:
            count();
            break;
        case 9:
            search();
            break;
       }
   }
}

void addatb(int n)
{
    struct node *temp;
    temp=(struct node *)malloc(sizeof(struct node));

    temp->data=n;

    if(p==NULL)
    {
        p=temp;
        temp->next=NULL;
    }
    else
    {
        temp->next=p;
        p=temp;
    }
}

void addate(int n)
{
    struct node *temp,*r;
    temp=(struct node *)malloc(sizeof(struct node));
    r=p;
    temp->data=n;

    if(p==NULL)
    {
        p=temp;
        temp->next=NULL;
    }
    else
    {
        while(r->next!=NULL)
        {
            r=r->next;
        }
        r->next=temp;
        temp->next=NULL;
    }
}

void addatg(int n)
{
    struct node *temp,*r;
    temp=(struct node *)malloc(sizeof(struct node));

    temp->data=n;
    r=p;
    int v;

    printf("\nAfter which point would you like to insert the value: ");
    scanf("%d", &v);

    if(p==NULL)
    {
         printf("\nList is empty\n");
    }
    else
    {
        while(r->data!=v)
        {
            r=r->next;
        }
        temp->next=r->next;
        r->next=temp;
    }
}

void display()
{
    struct node *r;
    r=p;

    if(p==NULL)
    {
        printf("\nList is empty\n");
    }
    else
    {
        while(r!=NULL)
        {
            printf("\n%d", r->data);
            r=r->next;
        }
    }
}

void delatb()
{
    struct node *r;
    r=p;

    if(p==NULL)
    {
         printf("\nList is empty\n");
    }
    else
    {
        p=p->next;
    }
}

void delate()
{
    struct node *r,*r1;

    r=p;

    if(p==NULL)
    {
         printf("\nList is empty\n");
    }
    else
    {
        if(r->next!=NULL)
        {
            while(r->next!=NULL)
            {
                r1=r;
                r=r->next;
            }
                r1->next=NULL;
            }
        else
        {
            p=NULL;
        }
    }
}

void delofg()
{
    struct node *r,*r1;

    r=p;

    int v;

    printf("\nEnter value after which to delete node: ");
    scanf("%d", &v);

    if(p==NULL)
    {
         printf("\nList is empty\n");
    }
    else
    {
        while(r->data!=v)
        {
            r1=r;
            r=r->next;
        }
        r1->next=r->next;
    }
}

void count()
{
    struct node *r;

    r=p;

    int f=1;


    if(p==NULL)
    {
         printf("\nList is empty\n");
    }
    else
    {
        while(r->next!=NULL)
        {
            f++;
            r=r->next;
        }
        printf("%d", f);
    }
}

void search()
{
    struct node *r;

    r=p;

    int f=1;
    int v;

    printf("\nEnter value after which to be found: ");
    scanf("%d", &v);

    if(p==NULL)
    {
         printf("\nList is empty\n");
    }
    else
    {
        while(r->data!=v)
        {
            r=r->next;
            f++;
        }
        printf("\n%d is located at node %d", v,f);
    }
}
