/********************************************************************************************
**    Name:main.c
**    Used to study the multithread programming in Linux OS
**    Author:<jufeng liu>
**    Date:2019/7/8        
**    Copyright (c) 2019,All Rights Reserved!
*********************************************************************************************/

#include <stdio.h>
#include <pthread.h>

void *myThread1(void)
{
    int i = 0;
    for(i=0; i<5; i++)
    {
	printf("This is the 1st pthread,created by x-hui.\n");
	sleep(1);//Let this thread to sleep 1 second,and then continue
    }
}

void *myThread2(void)
{
	int i;
	for (i=0; i<5; i++)
	{
	    printf("This is the 2st pthread,created by x-hui.\n");
	    sleep(1);
	}
}

int main()
{
	int i=0, ret=0;
	pthread_t pid1,pid2;
 
	ret = pthread_create(&pid1, NULL, (void*)myThread1, NULL);
	if (ret)
	{
	    printf("Create pthread error!\n");
	    return 1;
	}

	ret = pthread_create(&pid2, NULL, (void*)myThread2, NULL);
	if (ret)
	{
	    printf("Create pthread error!\n");
	    return 1;
	}
 
	pthread_join(id1, NULL);  //MainThead wait to exit,or else BrotherThead will crash
	pthread_join(id2, NULL);

	return 0;
}