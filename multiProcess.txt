/********************************************************************************************
**    Name:main.c
**    Used to study the multiprocess programming in Linux OS
**    Author:<jufeng liu>
**    Date:2019/7/8        
**    Copyright (c) 2019,All Rights Reserved!
*********************************************************************************************/
#include <stdio.h>

#include <stdlib.h>

#include <sys/types.h>

#include <unistd.h>
 

int main()

{

    pid_t pid;
             
      
    printf("My parent process id = %d\n", getppid());

    if ((pid = fork()) < 0)
        
    {
                
        printf("fork failed.\n");
  
        return 1;
    }
    else if (pid == 0)
    { 
       printf("This is child process. child process id = %d, parent process = %d, pid = %d\n", getpid(), getppid(), pid);
    }    
    else 
    {
        printf("This is parent process. parent process = %d, pid = %d\n", getpid(), pid);
        sleep(1);
    }                
       
    return 0;

} 
