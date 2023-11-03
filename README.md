# OS-EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS
## CONTIGUOUS ALLOCATION
## AIM:
To implement Contiguous File allocation Methods in C program.

## ALGORITHM:
1. Define a function recurse to allocate files on a disk using the First Fit technique, taking an array to represent free disk blocks.
2. In the recurse function, prompt the user to enter the starting block and length of a file to allocate.
3. Check if consecutive blocks starting from the user-defined block are free, allocate the file if they are, and print the allocated blocks.
4. If any of the blocks are not free, indicate that the file cannot be allocated contiguously.
5. After processing one file allocation, ask the user if they want to allocate more files; if yes, call the recurse function recursively; otherwise, exit the program.

## PROGRAM:
```C
#include <stdio.h>
#include <stdlib.h>
void recurse(int files[])
{
    int flag = 0, startBlock, len, j, k, ch;
    printf("Enter the starting block and the length of the files: ");
    scanf("%d%d", &startBlock, &len);
    for (j = startBlock; j < (startBlock + len); j++)
    {
        if (files[j] == 0)
            flag++;
    }
    if (len == flag)
    {
        for (int k = startBlock; k < (startBlock + len); k++)
        {
            if (files[k] == 0)
            {
                files[k] = 1;
                printf("%d\t%d\n", k, files[k]);
            }
        }
        if (k != (startBlock + len - 1))
            printf("The file is allocated to the disk\n");
    }
    else
    printf("The file is not allocated to the disk\n");
    printf("Do you want to enter more files?\n");
    printf("Press 1 for YES, 0 for NO: ");
    scanf("%d", &ch);
    if (ch == 1)
        recurse(files);
    else
        exit(0);
    return;
}
int main()
{
    int files[50];
    for (int i = 0; i < 50; i++)
        files[i] = 0;
    printf("Files Allocated are :\n");
    recurse(files);
    return 0;
}
```
## OUTPUT:
![output1](https://github.com/Shrruthilaya-Gangadaran/OS-EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS/assets/93427705/bb3f7532-9523-4aa1-9b90-c1c6f6d94baa)
## RESULT:
Thus, the implementation of Linked File allocation Methods in C program is done successfully.
## INDEXED ALLOCATION
## AIM:
To implement Indexed File allocation Methods in C program.

## ALGORITHM:
1. Define an array to represent disk blocks, as well as variables and functions for managing file allocation within index blocks.
2. In the recurse1 function, ask the user for an index block, check if it's already allocated, and prompt for the number of files needed.
3. In the recurse2 function, allow the user to select blocks for file allocation within an index block, check if they are available, and allocate the files if free, printing the allocated files.
4. Handle cases where the selected blocks are already allocated and prompt the user to try again.
5. After allocating files, ask the user if they want to enter more files; if yes, call recurse1 to continue the process, or exit the program if no more files are to be allocated.

## PROGRAM:
```C
#include<stdio.h>
#include <conio.h>
#include<stdlib.h>
void main()
{
int f[50], index[50],i, n, st, len, j, c, k, ind,count=0;
for(i=0;i<50;i++)
f[i]=0;
x:printf("Enter the index block: ");
scanf("%d",&ind);
if(f[ind]!=1)
{
printf("Enter no of blocks needed and no of files for the index %d on the disk : \n", ind);
scanf("%d",&n);
}
else
{
printf("%d index is already allocated \n",ind);
goto x;
}
y: count=0;
for(i=0;i<n;i++)
{
scanf("%d", &index[i]);
if(f[index[i]]==0)
count++;
}
if(count==n)
{
for(j=0;j<n;j++)
f[index[j]]=1;
printf("Allocated\n");
printf("File Indexed\n");
for(k=0;k<n;k++)
printf("%d ------- >%d : %d\n",ind,index[k],f[index[k]]);
}
else
{
printf("File in the index is already allocated \n");
printf("Enter another file indexed");
goto y;
}
printf("Do you want to enter more file(Yes - 1/No - 0)");
scanf("%d", &c);
if(c==1)
goto x;
else
exit(0);
getch();
}
```
## OUTPUT:
![output2](https://github.com/Shrruthilaya-Gangadaran/OS-EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS/assets/93427705/aec236a9-05aa-4a0b-b7ff-bd97a3373807)
## RESULT:
Thus, the implementation of Indexed File allocation Methods in C program is done successfully.
## LINKED FILE ALLOCATION
## AIM:
To implement file management using Linked list.
## ALGORITHM:
1. The program initializes an array f to represent the free blocks on the disk and sets all blocks to 0 (free).
2. The user is asked to enter the number of blocks already allocated and then to input the blocks that are already allocated (marked as 1 in the f array).
3. It uses a label x to allow the user to repeatedly enter the starting block and length for files to allocate.
4. For each file, it checks if the starting block is free; if so, it allocates consecutive blocks and marks them as allocated (1) in the f array. It also prints the allocated blocks. If a block is already allocated, it continues to allocate the file in the next available block.
5. After allocating a file, the program asks if the user wants to enter more files (1 for Yes, 0 for No). If the user chooses to enter more files, it jumps to label x, allowing the process to repeat. If the user decides not to enter more files, the program exits.
## PROGRAM:
```C
#include <stdio.h>
#include <stdlib.h>
int main(){
    int f[50], p, i, st, len, j, c, k, a;
    for (i = 0; i < 50; i++)
        f[i] = 0;
    printf("Enter how many blocks already allocated: ");
    scanf("%d", &p);
    printf("Enter blocks already allocated: ");
    for (i = 0; i < p; i++) {
        scanf("%d", &a);
        f[a] = 1;
    }
x:
    printf("Enter index starting block and length: ");
    scanf("%d%d", &st, &len);
    k = len;
    if (f[st] == 0)
    {
        for (j = st; j < (st + k); j++){
            if (f[j] == 0){
                f[j] = 1;
                printf("%d-------->%d\n", j, f[j]);
            }
            else{
                printf("%d Block is already allocated \n", j);
                k++;
            }
        }
    }
    else
        printf("%d starting block is already allocated \n", st);
    printf("Do you want to enter more file(Yes - 1/No - 0)");
    scanf("%d", &c);
    if (c == 1)
        goto x;
    else
        exit(0);
    return 0;
}
```
## OUTPUT:
![output6](https://github.com/Shrruthilaya-Gangadaran/OS-EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS/assets/93427705/a7b71226-8ebf-4b67-a15a-72e3ec53ff07)
## RESULT:
Thus, the implementation of Linked File allocation Methods in C program is done successfully.
## SEQUENTIAL FILE ALLOCATION
## AIM:
To implement Sequential File allocation Methods in C program.
## ALGORITHM:
1. Define an array to represent free blocks on a disk and create a function recurse for handling file allocation.
2. In the recurse function, ask the user for the starting block and length of files they want to allocate.
3. Check if the specified blocks are available for the entire file length, and allocate the file if they are, marking the blocks as allocated.
4. If the required blocks are not available for the entire file length, inform the user that allocation is not possible.
5.  After allocating a file, ask the user if they want to allocate more files (1 for yes, 0 for no), and either call recurse again or exit the program accordingly.
## PROGRAM:
```C
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
void recurse(int files[]){
    int flag = 0, startBlock, len, j, k, ch;
    printf("Enter the starting block and the length of the files: ");
    scanf("%d%d", &startBlock, &len);
    for (j=startBlock; j<(startBlock+len); j++){
        if (files[j] == 0)
            flag++;
    }
    if(len == flag){
        for (int k=startBlock; k<(startBlock+len); k++){
            if (files[k] == 0){
                files[k] = 1;
                printf("%d\t%d\n", k, files[k]);
            }
        }
        if (k != (startBlock+len-1))
            printf("The file is allocated to the disk\n");
    }
    else
        printf("The file is not allocated to the disk\n");
    printf("Do you want to enter more files?\n");
    printf("Press 1 for YES, 0 for NO: ");
    scanf("%d", &ch);
    if (ch == 1)
        recurse(files);
    else
        exit(0);
    return;
}
int main()
{
int files[50];
for(int i=0;i<50;i++)
files[i]=0;
printf("Files Allocated are :\n");

recurse(files);
getch();
return 0;
}
```
## OUTPUT:
![output5](https://github.com/Shrruthilaya-Gangadaran/OS-EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS/assets/93427705/c9e1aa9c-c6e2-419b-83ee-4a8db7b30bbc)
## RESULT:
Thus, the implementation of Sequential File allocation Methods in C program is done successfully.
