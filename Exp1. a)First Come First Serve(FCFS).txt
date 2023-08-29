#include <stdio.h>
int main()
{
	int i,n,bt[20],wt[20],tat[20],p;
	float wtavg,tatavg;
	printf("\nEnter the number of processes..");
	scanf("%d",&n);
	for(i=1;i<=n;i++){
		printf("\nEnter the Burst time for process %d...",i);
		scanf("%d",&bt[i]);
	}
	wt[1]=wtavg=0;
	tat[1]=tatavg=bt[1];
	for(i=2;i<=n;i++){
		wt[i]=wt[i-1]+bt[i-1];
		tat[i]=tat[i-1]+bt[i];
		wtavg=wtavg+wt[i];
		tatavg=tatavg+tat[i];
	}
	printf("\t PROCESS \t BURSTTIME \t WAITINGTIME \t TURNAROUNDTIME\n");
	for(i=1;i<=n;i++){
		printf("\n\t p%d \t\t %d \t\t %d \t\t %d",i,bt[i],wt[i],tat[i]);
	}
	printf("\nAverage waiting time is -- %f",wtavg/n);
	printf("\nAverage turnaround time is --%f",tatavg/n);
} 