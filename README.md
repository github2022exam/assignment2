# assignment2
to create a process in unix using fork() system call 
#include <stdio.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include<stdlib.h>
void bubblesort()
{
int i,j,a[50],n,temp;
printf("\nBubble sort\n");
printf("Enter size of array:-");
scanf("%d",&n);
printf("Enter array Element:-");
for(i=0;i<n;i++) 
{
scanf("%d",&a[i]);
}
for(i=1;i<n;i++)  //pass 
{
for(j=0; j<n-1; j++)  //swapping the array elements
{
if(a[j]>a[j+1])
{
int temp;
temp=a[j];
a[j]=a[j+1];
a[j+1]=temp;
}
}
}
printf("\nSorted array is:-\n"); //display sorted data
for(i=0;i<n;i++)
{
printf("%d\n",a[i]);
}
}
void selectionsort()
{
int i,j,a[50],n,min;
printf("Selection sort\n");
printf("\nEnter size of array:-");
scanf("%d",&n);
printf("Enter the Array element:-");
for(i=0;i<n;i++)
{
scanf("%d",&a[i]);
}
 for (i = 0; i < n-1; i++)
 { 
min= i;
 for (j =i+1; j < n; j++)
 if (a[j] < a[min])
 min= j;
if(i<min)
{
int temp;
temp=a[min];
a[min]=a[i];
a[i]=temp;
}
}
printf("\nSorted array is\n"); //dispaly sorted data
for(i=0;i<n;i++)
{
printf("%d\n",a[i]);
}
}
int main()
{
	int pid;
	pid=fork();
	if(pid<0)
	{
		printf("\nInvalid Process");
	}
	else if(pid==0)
	{
		printf("Child Process\n");
		printf("Child Pid : %d\n", getpid());
		selectionsort();
	}
	else if(pid>0)
	{
		printf("Parent Process\n");
		printf("Parent Pid = %d\n",getpid());
		wait(NULL);
		bubblesort();
	}
}
