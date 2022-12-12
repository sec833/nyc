# nyc

https://drive.google.com/file/d/12xhPWrsPw8qundbYYZuKSvm4G8lUz0O2/view?usp=sharing

## CS/FCFS:
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++)
{
printf("p % d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1;
//contains process number
}
wt[0]=0;
//waiting time for first process will be zero
//calculate waiting time
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n;
//average waiting time
total=0;
printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i];
//calculate turnaround time
total+=tat[i];
printf("\np%d\t\t %d\t\t
%d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat=(float)total/n;
//average turnaround time
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
}
```
## CS/SJF
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++){ printf("p%d:",i+1); scanf("%d",&bt[i]); p[i]=i+1; }
//sorting burst time in ascending order using selection sort
for(i=0;i<n;i++){
pos=i;
for(j=i+1;j<n;j++){ if(bt[j]<bt[pos]) pos=j;}
temp=bt[i];
bt[i]=bt[pos];
bt[pos]=temp;
temp=p[i];
p[i]=p[pos];
p[pos]=temp;}
wt[0]=0;
//waiting time for first process will be zero
//calculate waiting time
for(i=1;i<n;i++){ wt[i]=0;
for(j=0;j<i;j++) wt[i]+=bt[j];total+=wt[i];}avg_wt=(float)total/n;
//average waiting time
total=0;
printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i];
//calculate turnaround time
total+=tat[i];
printf("\np%d\t\t %d\t\t
%d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat=(float)total/n;
//average turnaround time
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
}
```
## CS/PS
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],pri[20],i,j,k,n,total=0,pos,temp; float
avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++){
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1;
//contains process number}
printf(" enter priority of the process ");
for(i=0;i<n;i++){
p[i] = i;
//printf("Priority of Process");
printf("p%d ",i+1);scanf("%d",&pri[i]);}
for(i=0;i<n;i++)
for(k=i+1;k<n;k++)
if(pri[i] > pri[k]){
temp=p[i];
p[i]=p[k];
p[k]=temp;
temp=bt[i];
bt[i]=bt[k];
bt[k]=temp;
temp=pri[i];
pri[i]=pri[k];
pri[k]=temp;
}wt[0]=0;
//waiting time for first process will be zero
//calculate waiting time
for(i=1;i<n;i++){wt[i]=0; for(j=0;j<i;j++) wt[i]+=bt[j]; total+=wt[i]; }
avg_wt=(float)total/n;
//average waiting time
total=0;
printf("\nProcess\t
Burst Time \tPriority \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++){
tat[i]=bt[i]+wt[i];
//calculate turnaround time
total+=tat[i];
printf("\np%d\t\t %d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],pri[i],wt[i],tat[i]);}
avg_tat=(float)total/n;
//average turnaround time
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);}
```
## CS/RR
```
#include<stdio.h>
main()
{
int st[10],bt[10],wt[10],tat[10],n,tq; int
i,count=0,swt=0,stat=0,temp,sq=0;
float awt,atat;
printf("enter the number of processes");
scanf("%d",&n);
printf("enter the burst time of each process /n");
for(i=0;i<n;i++)
{
printf("p%d",i+1);
scanf("%d",&bt[i]);
st[i]=bt[i];
}
printf("enter the time quantum");
scanf("%d",&tq);
while(1)
{
for(i=0,count=0;i<n;i++)
{
temp=tq;
if(st[i]==0)
{
count++;
continue;
}
if(st[i]>tq)
st[i]=st[i]-tq;
else
if(st[i]>=0){
temp=st[i];
st[i]=0;
}
sq=sq+temp;
tat[i]=sq;
}
if(n==count)
break;
}
for(i=0;i<n;i++)
{
wt[i]=tat[i]-bt[i];
swt=swt+wt[i];
stat=stat+tat[i];
}
awt=(float)swt/n;
atat=(float)stat/n;
printf("process no\t burst time\t waiting time\t turnaround time\n");
for(i=0;i<n;i++)
printf("%d\t\t %d\t\t %d\t\t %d\n",i+1,bt[i],wt[i],tat[i]); 
printf("avg time=%f,avg turn around time=%f",awt,atat);
}
```
## IPC/PIPE:
```
#include <stdio.h>
int main()
{
int fd[2],child; char a[10];
printf("\n Enter the string:");
scanf("%s",a);
pipe(fd);
child=fork();
if(!child)
{
close(fd[0]);
write(fd[1],a,5); wait(0);
}
else
{
close(fd[1]);read(fd[0],a,5);
printf("The string received from pipe is: %s",a);
}
return 0;
}
```
## IPC/SYSTEM CALL READ WRITE CREATEFORKOPENCLOSE:
```
#include<sys/stat.h>
#include<stdio.h>
#include<fcntl.h>
#include<sys/types.h>
int main()
{
int n,i=0;
int f1,f2;
char c,strin[100];
f1=open("data",O_RDWR|O_CREAT|O_TRUNC);
while((c=getchar())!='\n')
{
strin[i++]=c;
}
strin[i]='\0';
write(f1,strin,i);
close(f1);
f2=open("data",O_RDONLY);
read(f2,strin,0);
printf("\n%s\n",strin);
close(f2);
fork();
return 0;
}
```
## BANKERSALG:
```
#include<stdio.h>
int main (){
int allocated[15][15], max[15][15], need[15][15],
avail[15], tres[15], work[15], flag[15];
int pno, rno, i, j, prc,
count, t, total; count =0;
//clrscr ();
printf ("\n Enter number ofprocess:");scanf ("%d", &pno);
printf ("\n Enter numberofresources:");scanf ("%d", &rno);
for (i = 1; i <= pno; i++){ flag[i] = 0; }
printf ("\n Enter total numbers ofeach resources:");
for (i = 1; i <= rno; i++)
scanf ("%d", &tres[i]);
printf ("\n Enter Max resources foreach process:");
for (i = 1; i <= pno; i++){
printf ("\n for process %d:",i);
for (j = 1; j <= rno; j++)
scanf ("%d", &max[i][j]);
}printf ("\n Enter allocated resources for each
process:"); for (i = 1; i <= pno; i++){
printf ("\n for process %d:",i);
for (j = 1; j <= rno; j++)
scanf ("%d", &allocated[i][j]);}
printf ("\n available
resources:\n");
for (j = 1; j <= rno; j++){
avail[j] = 0;
total = 0;
for (i = 1; i <= pno; i++){
total += allocated[i][j];}
avail[j] =tres[j] -total;
work[j] =avail[j];
printf (" %d \t", work[j]); }
do{
for (i = 1; i <= pno; i++){
for (j = 1; j <= rno; j++){
need[i][j] = max[i][j] - allocated[i][j]; }
}printf ("\n Allocated matrix Max need");
for (i = 1; i <= pno; i++){ printf ("\n"); for (j = 1; j <= rno; j++){ printf ("%4d", allocated[i][j]); }
printf ("|");
for (j = 1; j <= rno; j++){
printf ("%4d", max[i][j]);}
printf ("|");
for (j = 1; j <= rno; j++){
printf ("%4d", need[i][j]);}}
prc = 0;
for (i = 1; i <= pno; i++){
if (flag[i] == 0){
prc = i;
for (j = 1; j <= rno; j++){
prc = 0; break; }
if (work[j] < need[i][j]){ } }
if (prc != 0)
break;
}if (prc != 0){
printf ("\n Process %d completed",i);
count++;
printf ("\n Available
matrix:")
for (j = 1; j <= rno; j++){
work[j] +=allocated[prc][j];
allocated[prc][j] = 0;
max[prc][j] = 0;
flag[prc] = 1;
printf (" %d", work[j]);}}}
while (count != pno && prc != 0);
if (count == pno)
printf ("\nThe system is in a safestate!!");
else
printf ("\nThe system is in an unsafestate!!");
return 0;
}
```
## DS/FCFS
```
#include <stdio.h>
#include <stdlib.h>
int main()
{
int RQ[100],i,n,TotalHeadMoment=0,initial;
printf ("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
for(i=0;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
printf("Total head moment is %d",TotalHeadMoment);
return 0;
}
```
## DS/SSTF:
```
#include<stdio.h>
#include<stdlib.h>
int main(){
int RQ[100],i,n,TotalHeadMoment=0,initial,count=0;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
while(count!=n)
{
int min=1000,d,index;
for(i=0;i<n;i++){
d=abs(RQ[i]-initial);
if(min>d){
min=d;
index=i;}}
TotalHeadMoment=TotalHeadMoment+min;
initial=RQ[index];
RQ[index]=1000;
count++;}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
## DS/SCAN
```
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
printf("Enter total disk size\n");scanf("%d",&size);
printf("Enter the head movement direction for high 1 and for low 0\n");
scanf("%d",&move);
for(i=0;i<n;i++){
for(j=0;j<n-i-1;j++){
if(RQ[j]>RQ[j+1]){
int temp;
temp=RQ[j];
RQ[j]=RQ[j+1];
RQ[j+1]=temp;}}}
int index;
for(i=0;i<n;i++){
if(initial<RQ[i]){
index=i;
break;}}
if(move==1){
for(i=index;i<n;i++){
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];}
// last movement for max size
TotalHeadMoment=TotalHeadMoment+abs(size-RQ[i-1]-1);
initial = size-1;
for(i=index-1;i>=0;i--){
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];}}
else{
for(i=index-1;i>=0;i--){
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];}
TotalHeadMoment=TotalHeadMoment+abs(RQ[i+1]-0);initial =0;
for(i=index;i<n;i++){
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];}}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
## DS/LOOK:
```
#include<stdio.h>
#include<stdlib.h>
int main(){
int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
printf("Enter total disk size\n");
scanf("%d",&size);
printf("Enter the head movement direction for high 1 and for low 0\n");
scanf("%d",&move);
for(i=0;i<n;i++)
{for(j=0;j<n-i-1;j++){
if(RQ[j]>RQ[j+1]){
int temp;
temp=RQ[j];
RQ[j]=RQ[j+1];
RQ[j+1]=temp;}}}
int index;
for(i=0;i<n;i++){
if(initial<RQ[i]){
index=i;
break;}}
if(move==1){
for(i=index;i<n;i++){
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];}
for(i=index-1;i>=0;i--){
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];}}
else{
for(i=index-1;i>=0;i--){
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i] ;}
for(i=index;i<n;i++){
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];}}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
