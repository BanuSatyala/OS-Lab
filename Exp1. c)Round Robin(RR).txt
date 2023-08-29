#include <stdio.h>
int main()
{
	int p[20],bu[20],pri[20],wa[20],tat[20],i,j,n,temp,max,ct[20],t;
	float awt=0,att=0;temp=0;
	printf("\nEnter the number of processes..");
	scanf("%d",&n);
	for(i=0;i<n;i++){
	    p[i]=i;
		printf("\nEnter the Burst time for process %d...",i+1);
		scanf("%d",&bu[i]);
		ct[i]=bu[i];
	}
	printf("\nEnter the size of time slice...");
	scanf("%d",&t);
	max=bu[0];
	for(i=1;i<n;i++)
	if(max<bu[i])
	max=bu[i];
	for(j=0;j<(max/t)+1;j++)
	for(i=0;i<n;i++)
	if(bu[i]!=0)
	if(bu[i]<=t){
	    tat[i]=temp+bu[i];
	    temp=temp+bu[i];
	    bu[i]=0;
	}
	else{
	    bu[i]=bu[i]-t;
	    temp=temp+t;
	}
	for(i=0;i<n;i++){
	    wa[i]=tat[i]-ct[i];
	    att+=tat[i];
	    awt+=wa[i];
	}
	printf("\t PROCESS \t BURSTTIME \t WAITINGTIME \t TURNAROUNDTIME\n");
	for(i=0;i<n;i++){
		printf("\n\t p%d \t\t %d \t\t %d \t\t %d",i+1,ct[i],wa[i],tat[i]);
	}
	printf("\nAverage waiting time is -- %f",awt/n);
	printf("\nAverage turnaround time is --%f",att/n);
} 
