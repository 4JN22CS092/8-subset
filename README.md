# 8-subset

Subset Sum Algorithm
#include<stdio.h>
#include<conio.h>
void subset(int,int,int);
int count=0,d,s[10],x[10];
void main()
{
int sum=0, i,n;
printf("\n enter no. of elements:\t");
scanf("%d",&n);
printf("\n enter the elements in ascending order:\n");
for(i=0;i<=n-1;i++)
{
scanf("%d",&s[i]);
}
printf("\n enter the required sum:\t");
scanf("%d",&d);
for(i=0;i<=n-1;i++)
{
sum=sum+s[i];
}
if(sum<d||s[0]>d)
{
printf("no solution exists\n");
}
else
{
subset(0,0,sum);
}
}
void subset(int m,int k,int sum)
{
int i;
x[k]=1;
if(m+s[k]==d)
{
printf("\n subset solution %d is\n",++count);
for(i=0;i<=k;i++)
{
if(x[i]==1)
{
printf("%d\t",s[i]);
}
}
}
else if(m+s[k]+s[k+1]<=d)
{
subset(m+s[k],k+1,sum-s[k]);
}
if((m+sum-s[k]>=d)&&(m+s[k+1]<=d))
{
x[k]=0;
subset(m,k+1,sum-s[k]);
}
if(count==0)
printf("no solution exists\n");
}
