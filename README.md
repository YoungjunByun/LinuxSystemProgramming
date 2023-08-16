# LinuxSystemProgramming
<aside>
👉🏻 <Contents>

</aside>

# 1. System Programming Concepts

-Linux kernel is loaded right after the bootloader. And then Kernel handles all things from then on.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1b9085fd-4612-40f0-b904-c085b65f819b/Untitled.png)

-System calls called through library functions and then internally the system calls work

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/78432065-62dc-47ec-a5df-a0cfacb10d0c/Untitled.png)

# 2. File Operations

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d5da67ce-b353-4c6a-b5e1-44ebdd1ffafa/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f747987-7510-417a-8378-ba9c6d321ee1/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0b4973c9-4c30-4b3d-98d9-0787eca9d80f/Untitled.png)

[open_1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f3d41fce-2ea5-4067-b68e-529419eef83f/open_1.c)

[open_2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7632e08a-b458-4fe6-9c3e-95c4c7e8647a/open_2.c)

[open_3.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0707523c-c40a-4703-8e6b-4f64903248c8/open_3.c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ae3263a3-cfe2-4d93-b0ac-f2e2f0abffba/Untitled.png)

[read.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/16d19d5e-b201-41c0-b237-e2ea4168af56/read.c)

-Buffer is made in user space. Not in the kernel space.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/49ee0661-0985-40e2-8f99-c4c2099e4583/Untitled.png)

[write1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e8795429-19f0-4e9c-a6b0-570c4ff6dfff/write1.c)

[write2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c42155ae-6c19-476f-8a21-e19f29736117/write2.c)

[write3.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b1434478-a810-4a5a-8084-00c282fd6a2c/write3.c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/43e72ed9-c82d-43eb-bc07-ef6aa562a6df/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/389e58a3-c1d7-49f5-b554-214bbb7ba946/Untitled.png)

-lseek manipulates the location of Offset Indicator of fd(file descriptor)

# 3. Advanced I/O

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/07c13376-6a13-4f73-b5a9-ae8f0654597f/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/de3a392a-32ba-4362-887c-fbd3d881627f/Untitled.png)

[race1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5965dd5b-fd7f-49ec-87db-87c0896035e4/race1.c)

[race2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9a0d89d8-57d6-4292-af9f-3babeb92b992/race2.c)

[race_around1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/47db7fec-98db-4ee1-8daa-849c72e77585/race_around1.c)

[race_around2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c453741a-6d54-474b-afe7-fb1a5f461488/race_around2.c)

-To execute both programs at the same time, use shell script.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2b9c8ebe-436c-4934-bb0b-9de658f90ee7/Untitled.png)

-Unexpected result occured. Everytime you run the shell script, It will give you different results. So, it is very unexpected.

-It means there is a race between each program to access the data and resource.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1d6cd033-733d-457d-8398-a08745762ea9/Untitled.png)

-Shortly Atomicity is the concept to protect Linux from Race Condition

-Atomicity makes only one process can be entered in Critical Section only in one given time.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4592090d-9aa1-4e44-8750-f6a24b119c00/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/30a3920a-6dac-4c94-9967-384e4666f8db/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/53c6c747-e751-489d-af63-d9748bf68c85/Untitled.png)

-Every process has its own file descriptor table.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dac5fae1-c534-414b-b52c-207f71612094/Untitled.png)

-Open file table is System Wide so that it is visible to all the process

-File Descriptor Table points to Open File Table and Open File Table points to i-Node Table which is the representation of a file.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6958252f-803f-4cef-a656-37ce5f070dec/Untitled.png)

-4KB block size is the default block size in Linux

-12 pointers altoghter it is 48KB of data

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48dcf5bf-910f-4ad7-af5c-8179d32ff88c/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d3206cba-29c1-4f6a-bac8-e45bc5127f45/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3634fe06-8875-42ba-9977-800e5f524331/Untitled.png)

-If the file size is more than 48KB then the Single Indirection will come up.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8e44a866-0634-4f2e-a135-53054d942632/Untitled.png)

-pointer only takes 4 bytes

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/731597ff-07db-4279-87bb-0c39a0e3de17/Untitled.png)

-CPU uses multiple stack pointer tables to store big size of files.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc4b7f26-b241-4839-831c-4ee8ad958214/Untitled.png)

[dup_1a.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7c640b16-173a-4716-b14b-d136b70d5582/dup_1a.c)

[dup_1b.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93fe1954-0af4-4ddb-9ca4-cdd5d84e9b0e/dup_1b.c)

[dup2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3176754c-db4d-4aba-8076-8bf3694937f9/dup2.c)

-If you use dup command in the source code. It will be added on the File descriptor table and point the same slots of open file table.

# 4. Introduction to Process

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/95b12229-3f29-4017-b078-42ef2a150052/Untitled.png)

-Process VS Program

Process is an instance of an executing program whereas Program is a file containing a range of information that describes how to construct a process at run time

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d6ed83c-a3e6-4d9f-809d-b02dd2ba96cc/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/926cfa23-0ce2-4970-a835-72e4b83036d1/Untitled.png)

-getppid is parent process’s PID.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b7775707-37ca-44ef-84df-2d5868010642/Untitled.png)

-pid can variable based on the run time process id but ppid is fixed.

-That terminal is the parent process

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1072dd3b-e28e-4e2b-a427-588d28505e11/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c2283b9e-a2a6-4752-8374-ee8c8631112a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5ad18862-339a-45f7-8e4b-2fb548ccb137/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/66aa6949-48c2-4acf-9b6a-5b6bcb9ce7a1/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ec3349e8-017f-4c39-b5ff-f98dc1e2ee59/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b670209e-567d-4771-b635-636bfcf619d6/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/72c08c7f-671d-4dff-983b-23dd8c8f4529/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f5f58d5-b65f-42b0-b075-cdcc39e96407/Untitled.png)

Summary

1. ps -ef  :  can be used to list all running process.

2. Each process has a unique ID called as Process ID (PID in short)

3. Every Process has a parent Process (PPID)

4.  PID - '0' is swapper process

5.  PID - '1' is INIT process

6. Each Process has its own memory space, i.e

a. Text/code segment

b. Data segment(Global and Static variables)

c.  Stack segment(local variables)

d.  Heap segment(Dynamic allocation)

# 5. Virtual Memory of Process

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/64d0d2c7-3888-435b-aff2-c5c99c935a6c/Untitled.png)

-Virtual memory is to give more usable space than physical RAM

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7b761f15-8adb-4112-8a77-a7e519da2f72/Untitled.png)

-physical memory(RAM) is the place instructions are stored. And then CPU access instructions is RAM

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/df514f81-2700-4464-86cf-e5ba0b85c576/Untitled.png)

-The size of virtual memory of process is 4GB. Every process has a 4GB of virtual memory

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d9b26c9e-dc9d-4735-9785-0e6f532cee2f/Untitled.png)

-swap area = disk table

-4GB(virtual memory of each process)is split into 4KB size of page. And similarly, RAM(Physical memory) is also divided into a series of page frames which is 4KB

-Resident Set = some of the pages of a process are present in RAM(Physical memory)  ===⇒ The rest of pages of a process are in the swap space(=disk space) and they are loaded into RAM(physical memory) when needed.

-Frame = Page Frame ====⇒In linux, default page frame size is 4k

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cb6521d7-0f7c-4eef-a338-784358baf8ff/Untitled.png)

-Main intention of Page Table is to indicate which page frames of RAM(Physical Memory) match to which pages of a process.

-Page 4 above can be residing in the swap space.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e0cdc0bb-b82e-432b-b562-c243dc9078aa/Untitled.png)

-Memory sharing is done by using page table.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45631b1c-3917-4ac0-aaa0-513016a7541f/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dcc69ea1-a6ed-44d9-a66b-3ead75de0384/Untitled.png)

-Page Fault can happen in both situation of accessing pyhsical memory(RAM) or accessing page table

-To protect and prevent this kind of page Fault, if the page table or physical memory(RAM) is already full, then pages of a process can first be loaded in Swap Space and then be added into RAM(Physical Memory)

[cli1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/827303fa-12c4-4319-9084-8f102011c880/cli1.c)

[cli2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c734a17f-9bc8-4afd-8fea-e25f1559897a/cli2.c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7fb3002c-ed81-4e7f-8884-c121c60c4dbb/Untitled.png)

-argc, *argv[] arguments get the arguments from the shell.

These go to stack part of the virtual memory of process.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8f726285-6ad3-435c-89bc-e4fb2f3a5833/Untitled.png)

-This parameter is very useful when user directly gives input of arguments and executes at the same time

-This parameter forms a stack frame of the main fuction

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/33bddf7b-f924-4cd9-b60d-a97295966c35/Untitled.png)

-every process can excess environment

[env1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9c6e978-5862-4748-8934-2cee8ea20368/env1.c)

[env2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57d396f9-bdec-4fce-9ac2-6d8c39b53bb8/env2.c)

[env3.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ee582a4-4469-4721-9914-8338fb8b493d/env3.c)

Virtual memory in Linux

---

1. It gives a virtual feeling for each process, that it own the complete Physical memory(i.e RAM).
2. It gives virtual feeling to each process, that it can have more memory than the available Physical memory.
3. Physical memory is Real memory(It does exist)
4. Virtual memory is a conceptual memory(It is only like a imaginary memory )
5. CPU executes code/instruction from Physical memory(and not from virtual memory)
6. Each process hold instructions/code, data, stack, heap in the imaginary Virtual memory, this data/instruction is copied to real memory(Physical memory) at time of execution.

Page Table

---

1. Each process has its own page table.
2. When the Process copies data/instruction (contents of page memory) from virtual memory to Physical memory, it creates a entry of that particular Virtual memory's Page in 'page table'.
3. This Page table entry will inform CPU whether, the required data from each process's virtual memory is present in Physical RAM or not.
4. The Page in Physical memory can be swapped in/out from/to secondary memory(like hard disk or equivalent). Swap Space includes every form of secondary memory like HDD
5. When page from Physical memory is copied to secondary memory, the Page table entry of that particular page is deleted, similarly, when page data is copied from secondary memory back to physical memory, a entry in page table is made for that particular page.

NOTE: Physical memory refers to RAM memory

What is Page Fault?

Page fault is kind of indication informing system that the required page of memory was not present on the corresponding Process's 'Page table', and this page of memory needs to be copied on to  Physical memory for further instruction/data processing.

Note: Page Fault occurs for a "running Process" when its required page is not present in Physical memory.

# 6. Memory Allocation

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ee24ac89-dea1-4fb7-90cd-73b226add9ab/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/22ab5f6a-7104-4d22-a32f-c30e8d4372f1/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/09a1bf91-55d7-4664-be53-96adb2962dc0/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cc41dd56-e1bd-44d1-8618-f85f1ed20fd9/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/06e47c70-29c3-4a6c-a54f-9009f22d6beb/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5fc57daf-a02a-4c7d-94cb-f4a3f45e0c6d/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e024363d-7df9-46e8-bc2d-abee8d742fed/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5dbf281c-ad2d-4a81-8751-134a768eeb6b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fc4f3896-aa3e-487b-b6b8-9e82a62d81b2/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0f8ffe39-e5bf-458c-a639-9282d1681cc0/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/68eda49c-de20-4aff-bd75-a7091fbdb867/Untitled.png)

-When the process is done, stack is freed which means alloca() does not require to free it intentionally. But we need to always be very careful to do not use alloca() all the time-it can cause stack overflow if the size of stack grows a lot.

[calloc.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d80ccc2f-8345-4bc7-9934-8cf3efc2998c/calloc.c)

[malloc.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/90dd321d-f6ce-4cfd-8876-8cf3bb3a16e0/malloc.c)

[realloc.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3ba7159c-a833-4f39-b83d-8d71c0c247eb/realloc.c)

Memory Allocation

- --------------------

1. Below  are widely used dynamic memory allocation **library calls (and not system calls)**

a.  malloc()

b.  calloc() - This function is same as malloc() but initializes the memory allocated with '0'

c.   realloc() - Is used if there is a need to change the size of already allocated memory.

2. Dynamic memory is allocated in 'Heap' segment

3.  All above functions return (void*) - pointer to allocated memory if success, NULL if failure

4.  syntax:

#include <stdlib.h>

void *malloc(size_t size);

void *calloc(size_t nmemb, size_t size);

void *realloc(void *ptr, size_t size);

5. free() is used for freeing the dynamically allocated memory

Syntax of free():      void free(void *ptr); // ptr variable points to the memory that needs to be freed.

6. Do not  call free() on same pointer (same memory location) twice.

7. After free(), it is good practice to assign the pointer to NULL(because the memory is already de-allocated, and the pointer now does not point to a valid memory location)

# 7. Process Programming

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a4bc24a0-1366-402a-8b5e-48646d9e1a5e/Untitled.png)

-The main intention of creating a process is we can break down a given bigger task into smaller tasks and let each process to accomplish the smaller task. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6e058520-da98-42f7-a95e-4b3d2ef03d51/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fa3b399e-2038-4ea3-b353-4b42bac6bc36/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a1481635-3b5c-487a-b80b-9ebf3a1667c7/Untitled.png)

[fork_1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5eee6cf1-a05d-4f9c-82d8-37623bf0822e/fork_1.c)

[fork_2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/948bbca6-aeab-4d69-abf3-b6f2ac93ffd3/fork_2.c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/80afb730-410f-44ad-ad6b-7492cc1a948a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f24dd0ed-a568-4ca3-a204-bffbdba782ef/Untitled.png)

-both parent and child continues or executes their programs from right below pork() command which means the child also copy pc(program counter) of the parent. child process thinks he`s id is 0.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4a7604d-16d9-4339-89ea-c8e664028a60/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8446e30a-8a3e-4c11-9adb-f86ffc21b202/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/14bd7710-9281-4e83-8bd4-de502fbd407c/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c93c3324-ecd6-4d7d-bb61-6d50155ab1e8/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b155169f-e814-462f-add5-fd3a9824b116/Untitled.png)

-Copy On Write = initially both parent and child share the same page. But right after the child alters the any parts of virtual memory, they start using two separate and different page.

# 8. Process Monitor

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0aca98c8-dc97-44c8-96a7-01781f67e805/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cc8e53b5-a4cb-43c4-8cbe-d2d9ac790e65/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d2dc795b-32ed-4afb-8c2a-1baec8abbb50/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/653a4407-44dd-4135-b0b2-bf19c61a3073/Untitled.png)

[wait_1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/47553848-03af-4834-8d97-7639abff8803/wait_1.c)

[wait_2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/12275258-a1ce-430b-9a4e-21a9000281c6/wait_2.c)

[waitpid_3.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/57bde999-e3d3-44ba-8f96-f925f29b72e9/waitpid_3.c)

[waitpid_4.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1fbc3000-d140-440b-900e-8a72b77dea2f/waitpid_4.c)

```
Process termination status (int) 16 bit number
1. status value if  child process has normal exit/termination
   15......8    |     7......0
   XXXXXXXX     |     XXXXXXXX
   exitStaus    |     0
-Only upper 8bits(1byte) is used to represent normal exit/termination

2. killed by signal
    15......8    |     7   ......0
    unused       |     X   termination signal
                       |
                       |-----> core dump flag
-Only lower 8bits(1byte) is used to represent normal exit/termination
```

-The parent process does not have the control to specify which child to wait. It just waits for any child process. But waitpid() command can specify which specific child to wait for.

-Process Synchronization like the ways above is the methods that we can control the process

-non-blocking does not stop.

[orphan.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/07f56799-7231-42a3-836b-c14dca0da03f/orphan.c)

[zombie1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/06d071b3-6fa7-45df-8510-2370a4709652/zombie1.c)

[zombie2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4ca1be9a-b50b-43ee-84fb-e5aa60e84850/zombie2.c)

-In Linux System, PID 0 becomes the parent of Orphan state of child process. That`s the reason why they have 0 as their ID above.

-When the child process exits, but if there are still process in the entry table, we call it zombie process.

-If the parent process dies and child process is alive, we call it orphan state. 

An orphan process is formed when it's parent dies while the process continues to execute, while zombie process is a process which has terminated but it's entry is there in the system.

## What is the Zombie process?

**Zombie process** is also known as ***"dead"*** process. Ideally when a process completes its execution, it's entry from the process table should be removed but this does not happen in case of zombie a process.

> Analogy: Zombie, mythological, is a dead person revived physically. Similarly, a zombie process in os is a dead process (completed its execution) but is still revived (it's entry is present in memory).
> 

!https://scaler.com/topics/images/zombie_process.webp

**Note:** Process table is a data structure in RAM to store information about a process.

## What happens with the zombie processes?

- wait() system call is used for removal of zombie processes.
- wait() call ensures that the parent doesn't execute or sits idle till the child process is completed.
- When the child process completes executing ,the parent process removes entries of the child process from the process table. This is called "reaping of child".

!https://scaler.com/topics/images/zombie_process_in_OS.webp

## Zombie Process Code Example

In this code given below, we'll see how a zombie process is created.

- The child process completes its execution by using exit() system call.
- So when the child finishes it's execution **‘SIGCHLD’** signal is delivered to the parent process by the kernel. Parents should,ideally, read the child's status from the process table and then delete the child's entry.
- But here the parent does not wait for the child to terminate , rather it does it's own subsequent job, i.e. here sleeping for 60 seconds.
- So the child's exit status is never read by the parent and the child's entry continues to remain there in the process table even when the child has died.

**Note:** Kernel sends a SIGCHLD signal to the parent process to indicate that the child process has ended ·

```css
// A C program to demonstrate Zombie Process.

#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>

int main()
{
	// Fork returns process id in parent process

    pid_t child_pid = fork();

	// Parent process
	if (child_pid > 0)
		sleep(60);

	// Child process
	else
		exit(0);

	return 0;
}

```

## Why are lots of zombie processes harmful to the system ?

A lot of zombie processes in os are harmful as

- The OS has one process table of finite size , so lots of zombie processes will results in a full process table.
- A full process table means that OS cannot create a new process when required and Zombie processes in os are of no use as the process has died but it's entry is occupying the space in memory

**An extreme case - Fork bomb** The program below creates an infinitely many zombie processes because the parent does not wait for it's child process.

```cpp
#include <unistd.h>
int main()
{
   while(1)
      fork();
   return 0;
}

```

!https://scaler.com/topics/images/zombie_process_example.webp

- PIDs in os are finite , when all the PIDs have been consumed by Zombie Process , no new process can be created.
- Solution : Reboot the system

## What is the Orphan Process?

We'll again use real life analogy to understand the orphan process.

- In the real world orphans are those children whose parents are dead.
- Similarly, a process which is executing (is alive) but it's parent process has terminated (dead) is called an orphan process.

## What will happen with the orphan processes?

- In the real world orphans are adopted by guardians who look after them.
- Similarly,the orphan process in linux is adopted by a new process , which is mostly init process (pid=1) . This is called ***re-parenting.***
- Reparenting is done by the kernel,when the kernel detects an orphan process in os, and assigns a new parent process.
- New parent process asks the kernel for cleaning of the PCB of the orphan process and the new parent waits till the child completes its execution.

!https://scaler.com/topics/images/orphan_process.webp

## Orphan Process Code Example

In the example,the parent process sleeps for 20 seconds while the child process sleeps for 30 seconds.

1. So after sleeping for 20 seconds the parent completes its execution while the child process is still there at least till 30 seconds.
2. When the child process becomes an orphan process , the kernel reassigns the parent process to the child process.
3. As a result the parent process id of the child process before and after sleep() will be different.

**Note:** Kernel is central component of an operating system that manages operations of computer and hardware.

```cpp
// C program to demonstrate Orphan process
#include<stdio.h>
#include <sys/types.h>
#include <unistd.h>

int main()
{
	int pid;
	pid = fork();

	if(pid == 0)
	{
		printf("I am the child, my process ID is %d\n",getpid());
		printf("My parent's process ID is %d\n",getppid());
		sleep(30);
		printf("\nAfter sleep\nI am the child, my process ID is %d\n",getpid());
                printf("My parent's process ID is %d\n",getppid());
		exit(0);
	}
	else
	{
		sleep(20);
		printf("I am the parent, my process ID is %d\n",getpid());
                printf("The parent's parent, process ID is %d\n",getppid());
		printf("Parent terminates\n");
	}
    return 0;
}

```

**Output**

```cpp
My parent's process ID is 32005
I am the parent, my process ID is 32005
The parent's parent, process ID is 31998
Parent terminates
After sleep
I am the child, my process ID is 32006
My parent's process ID is 1

```

## Why are too many Orphan processes harmful to the system?

- Orphan processes in OS hold resources when present the system.
- Orphan processes in a large number can overload the init process and hang-up a system.

## Conclusion

Let's go through what we have learnt till now.

- In linux OS, processes have parent child relationships.
- A zombie process in OS is one that has completed it’s execution but its entry in the process table.
- wait() system call is used to deal with zombie processes.
- An orphan process in OS is one which is executing but it’s parent process has terminated is called an orphan process.
- Kernel allocates a new process as parent process to orphan process. Mostly the new parent is the init process (pid=1).
- Too many zombie processes and orphan processes are harmful.

# 9. Advanced Process Programming

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c4659607-c3a8-4501-840a-cb2da3cb3713/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b2f3112b-9a24-4169-a69b-5178534f031c/Untitled.png)

[p1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dded5d0d-e34a-4d94-8fe0-85456e68024a/p1.c)

[p2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6840976b-3f1c-4b0c-ad9b-bc100e32601a/p2.c)

-But even after exec() command, it remains the same process.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cdf6a8a2-8fe7-43b2-85d3-e71813fe469e/Untitled.png)

[p1 (1).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2232ed7e-d132-43ae-ae88-d4e271cf7eac/p1_(1).c)

[p2 (1).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8f63722d-8dfb-4bcc-ab45-38e879f6a16f/p2_(1).c)

[program1.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/694eed3d-237c-4e07-a427-86f7d4608080/program1.c)

[program2.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/50919890-b0e9-4634-9efd-79e218843eb5/program2.c)

-exec() is usually used right after fork() 

[program1 (1).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a603184b-6824-4ecd-a548-71a281986060/program1_(1).c)

[program2 (1).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d619ccfb-8e89-4dc3-b99a-bc13b783b20f/program2_(1).c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9663f89a-8ee3-4c34-89e9-8e78909a80a0/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/932e997b-eea8-4c84-9506-8d77dd0d1b4a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8586ba97-d5bf-416e-ad69-12e4d16c3429/Untitled.png)

-PCB refers to Process Control Block

-PCB is unique to every single process.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ceafb5fc-9aac-4007-9f62-a56526ae6771/Untitled.png)

[CPUlator ARMv7 System Simulator](https://cpulator.01xz.net/?sys=arm)

-This link shows how CPU works. And the components of CPU in this website are recorded in PCB for real

-Linux is used in a multiprocessing system. So there are many processes running on a Linux system. So whenever the CPU time of a process is finished, the scheduler will schedul the other process in the queue. The old process when it resumes back, it needs to be resumed in the same state in which it was halted. So we have to save all the process state before it leaves the CPU. 

# 10. Signals

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f0040c5-99a9-4d85-9441-fbc4c7a2ba75/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/69b23cb0-6a8a-43cb-affa-16b37bb23475/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/72bfeb59-9f12-4853-bd1e-6e7fc25b1126/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f1f88947-a629-4275-ab02-56b41f91d991/Untitled.png)

-There are three distinctive actions that processor do when signal occurs. First, Ignore, Second, Catch and Handle. Third, Perform the default action.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6a7dd389-03ca-48df-901d-d64587ec19b0/Untitled.png)

-Signal is asynchronus so that it can occur at any time.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f4aa1bfd-7c47-4fcd-a236-486137b711c1/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/aa8a4543-1b7c-4b1a-86d9-aafbc121a14a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2d0d8eb6-decb-4ad3-a532-da6fe11745c5/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e0a620c-f00f-4ecd-8f39-3d0d7c0a7bcf/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ce6e312e-27f2-453a-9134-658345cf1e00/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9f646265-777e-45d3-abdf-6ff62a5c52d4/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e522c73-28c3-4260-b62c-8b35da50fca0/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c7a9cecd-2329-4289-8783-1569e7ad78e1/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/778c2ebc-ced4-41fa-bb2b-81a33a118a71/Untitled.png)

-Kill can give any signals to any process

[1_sig.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0b90a7af-255c-4b3c-8ea7-eacce4799f25/1_sig.c)

[2_sig.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9a08ddca-c6ec-410e-82e3-6270236a2a04/2_sig.c)

[3_sig.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/37679e61-f96e-4608-b13e-a0048f14481c/3_sig.c)

[4_alarm.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/09c980e7-14de-400a-b374-d88036884890/4_alarm.c)

-signal() command set the action which kernel must do when corresponding message come.

[program1 (2).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c154080b-3ce7-4013-901b-bfa99dba7574/program1_(2).c)

[program2 (2).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0df6abe0-cc76-4c2f-922c-91ff73337e41/program2_(2).c)

# 11. Threads

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/81bd36f9-5bf7-48f3-bc32-7938e67b7721/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e69a78e9-5c93-4f99-b574-8f9d7566bd66/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab90ad6a-45eb-4f32-83a1-55f8d146c5a5/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c3151559-c2ed-4bbc-b6a8-4efe804fe4ea/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4b6510f1-3f7c-4523-b13c-85052499f025/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/85bcca0a-4010-415f-9e41-087763edbbef/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b5aa124f-cb81-47c1-9f9d-73e7c7b2536b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f7bc0f0-0c49-484e-8137-e173ef5ede15/Untitled.png)

[1_thread_create.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3c1fcf09-6de2-496f-b79b-bc1450854f01/1_thread_create.c)

[2_thread_create.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc273b58-b2d9-4082-81c2-c41802f3bb82/2_thread_create.c)

-exit() finishes other threads but pthread_exit() can’t finish other threads

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/420042d1-5088-48cd-8837-29770890464a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e4750231-ae12-4a5a-83cc-eabfc42f399b/Untitled.png)

[3_thrjoin.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c722dcd7-6e0b-4e98-8349-20b2c733184b/3_thrjoin.c)

-In order to link with the pthread library, you must add -lpthread option when you’re compiling it.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/cf490be1-c5b2-41db-b40f-dcc99af065c3/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1c41ff00-d784-42bf-ab9a-d43bc8eed8cf/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d4805fc7-61c8-4b88-85a4-0d72b0d4c56a/Untitled.png)

[4_thrdetch.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dff6786f-2639-45ae-89ea-620a75350635/4_thrdetch.c)

[5_thrcancel.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9da492f7-c4a2-43b8-a914-e9293fb25548/5_thrcancel.c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5df25865-a5f3-46c4-9069-d08cc1cb3653/Untitled.png)

# 12. Thread Synchronisation

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/22637e48-8c08-4493-97a3-b7635ad83e51/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/55789cd1-7a08-4c4c-9ce3-46243527c4d8/Untitled.png)

[1_mut (1).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c5df3019-b876-48d4-b1fa-ec2d9922e475/1_mut_(1).c)

[2_mut (1).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/335bef55-90e5-4ffd-9076-3451d311b462/2_mut_(1).c)

[3_mut (1).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a0a83238-0f0e-47f0-b766-cbc5b87cc369/3_mut_(1).c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9d378e8c-fab0-4fdf-b62d-517dc34719c4/Untitled.png)

-We can see the result varies everytime due to synchronisation while accessing global value.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5b53b6ae-b285-4881-b4a8-ee5d05d3719c/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e7a73262-a871-4b3c-9207-74828e09cb9b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/28952e4a-4c99-469c-a85d-c0db4405aba9/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c70d6717-68fa-4c27-8f94-b5fd5a33c388/Untitled.png)

-Mutex is allocated as a static variable

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f4efed7-cad4-47f2-970b-622e98c51ab4/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9f8b7ca3-22f2-4569-a797-d2adcbac07dd/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d5bd2f82-5c9e-46b4-934f-48e6cdb4bbbd/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/93b69b46-81ed-41ac-8ebb-c872696dc5a5/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/46fa6526-dd0f-4136-8197-b04618f06a99/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/579d622d-696d-4ea7-987e-d139693da6b7/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/55bd3e5d-e740-446e-a29b-c7614bcd49fa/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9aeb7fd-3794-4cec-aafc-9fbfd87f7940/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/877b569b-b8dd-4fd4-897d-c3d8d2df70ee/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8705158a-42b3-4413-82a1-bab4f001c1a7/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ded83e6b-09ad-4341-b409-7d802dd0827e/Untitled.png)

[sig_cond.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/538f70d9-9517-4f8f-bfbf-fb292bc6cc7c/sig_cond.c)

```c
#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <unistd.h>

pthread_mutex_t my_mutex = PTHREAD_MUTEX_INITIALIZER;
pthread_cond_t myConVar = PTHREAD_COND_INITIALIZER;

int doneFlag = 0;
char buf[100];

/* Producer thread*/
void * threadA(void *p) {
    printf("\nthreadA Scheduled first\n");
    sleep(1);
    pthread_mutex_lock(&my_mutex);
    printf("\n threadA: critical section executes always first\n");

    /*producer will produce data here*/
    sprintf(buf,"This is data Buffer");
    doneFlag  = 1;
    pthread_cond_signal(&myConVar);
    pthread_mutex_unlock(&my_mutex);
}

#if 1
/* Consumer thread*/
void * threadB(void *p) {
    printf("\nthreadB Scheduled first\n");
    pthread_mutex_lock(&my_mutex);
    if (doneFlag == 0)
        pthread_cond_wait(&myConVar, &my_mutex);
    /*consumer will consume data here*/
    printf(" threadB: signal received from threadA, this is always executed after threadA critical section %d\n", doneFlag);
    printf("\nThe buffer received from producer thread is (%s)\n",buf);
    pthread_mutex_unlock(&my_mutex);

}
#endif

int main(int argc, char** argv) {
    srand(time(0));
    pthread_t pthreadA;
    pthread_create(&pthreadA, NULL, threadA, NULL);
    pthread_t pthreadB;
    pthread_create(&pthreadB, NULL, threadB, NULL);
    pthread_join(pthreadA,NULL);
    pthread_join(pthreadB,NULL);
    printf("\n Main thread is exiting now\n");
    return (EXIT_SUCCESS);
}
```

# 13. IPC

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/191b3bb4-6baf-428e-ae1f-a6660cadd722/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a45b3bd5-dab0-4a3a-af8a-20b1e026798e/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f75cfd1-0a4e-471a-8746-67ec40049850/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/107c483b-a06e-44d0-9164-c68d254f28a5/Untitled.png)

-Pipe is unidirectional.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7d8c3188-f6ff-4661-b2f8-fd2207a16587/Untitled.png)

-PIPE is like a buffer in kernel memory which has 64KB capacity

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/caccd2dc-7493-4a0d-b8a0-abff2ab85cd7/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e515001b-c0e5-475c-8564-f969d29ebc2b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dd65f953-3d70-48e1-bc50-7076b3c7b212/Untitled.png)

-Closing writing end of child process and reading end of the parent process

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/477b21cc-2fae-4e23-828c-2fac10b55a5c/Untitled.png)

[1_pipe.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5c7954c1-2dd2-4ebf-8892-e9413311d831/1_pipe.c)

[2_pipe_child.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0a516476-aab7-43f9-8541-b12ae5116958/2_pipe_child.c)

[3_pipe_child.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/94e5bc26-42d0-46dd-8cb1-20f29ccafa15/3_pipe_child.c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7e602c62-a8f1-4605-b7c4-e6a8c56c08cb/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9fee2258-4364-462c-87e7-625bfc6cda60/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9dd3c581-36c3-4936-b68f-a160cb489a5e/Untitled.png)

[1_write_fifo.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e7b3ec77-5099-46dd-9750-1f3f847bc448/1_write_fifo.c)

[2_read_fifo (1).c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/81c16282-e244-4dce-ac97-e4212f38af20/2_read_fifo_(1).c)

-FIFO can be used between unrelated process

-The file type is “p” for the new made file. So it is called “named pipe”

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f824828a-79f3-4125-892b-0d23e64cb9f9/Untitled.png)

[msg_q_rec.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b24d806f-a9af-4624-a8de-df9028ea9c5d/msg_q_rec.c)

[msg_q_send.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/812feacc-1cd6-424f-b546-6c1739e8b597/msg_q_send.c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e41b92e3-3a03-47ed-9422-25b08dbe213d/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b3129b33-5c2c-4bb0-ba1c-28e82f8772b5/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/211cfaa1-9e50-477c-9db2-32b7b1d03e0c/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc8f5d65-2a37-4202-a91c-0d176fede162/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d91d6d6a-d5b2-43ad-94e1-8f370f476dda/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2fdace30-7a91-4707-b27d-577e9b92e911/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c4bec2d5-587b-4c89-83e7-3fed053a1700/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/30a9d944-9bb7-4017-a4d8-d11a98a271e8/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3a55888c-59d5-4142-a89c-37734ee6e0e6/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9f41856-287d-448e-a5c7-038829f21e2d/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/322dd102-9620-4bc0-8ab5-2c9e530164c8/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d14f1180-1b22-49cc-9bc0-2bcb0c82af74/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e270cd17-4f69-4826-8860-0af03d6239e1/Untitled.png)

[1_sem.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a6a6883c-7e4d-42c8-a579-e3f6b6ae7899/1_sem.c)

[2_sem.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c3aaa263-d9e4-4656-9380-efcedd3abdd6/2_sem.c)

[3_sem.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/21e50d8d-6473-4825-b4a9-951f93e24b9f/3_sem.c)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0029da6e-e788-4d9b-9922-ee9bfe9b46f1/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c90a041c-e268-48e1-9054-4ff10fdec89b/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7dcae99f-81a3-4078-9ac6-3679ae6188d3/Untitled.png)

-semaphore is kind of a value which is used by process to synchronize usage of the critical section of shared memory

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d5f49446-4fce-47de-bb17-25c08db637db/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b29d1db4-105a-455f-ae59-5cb6ec7c56a7/Untitled.png)

-Named semaphore is a semaphore in which it is present on the file system. Whereas an unnamed semaphore is one which is present on the memory.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d10369e3-3e7b-4f72-a5d5-6e1d71144f66/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/979a41c1-6a41-4580-aad9-ed1942a3f272/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/56853200-996f-42ab-884a-4e5bd007e526/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5b02b7a9-2419-4c80-b17b-114ea2b88f04/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/50fa4a77-eda1-4aca-9ce3-6b64006764ff/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b3b6e155-adb0-4b35-b5c9-e524231ff16f/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f60bf203-0a9b-4172-8fe9-a34a1ab13e90/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7a356c78-3718-4f3f-b9b3-6f5cb34fd726/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/37ccf5e9-7913-4956-b456-28d6810db2de/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b0deb700-eaa7-4af4-882a-57a6ccba90bf/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ab257552-1def-43c4-b6a9-bf40154805fe/Untitled.png)

[1_shm_write.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/17c1358a-0e23-4fe9-a9b9-676845a24e0a/1_shm_write.c)

[2_shm_read.c](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/329d2b5c-eb0e-48ab-bd77-d12f51955ff1/2_shm_read.c)

-Shared memory is the fastest method of IPC

Q. What is Thread Local Storage (TLS) or Thread Private Data?

A.  Thread Local storage is the part of memory of each thread, in which the variables are accessed by all functions belonging to that thread. It acts like a variables that are global and visible only to specific thread where it is defined.

```
  Functions/data structures involved in creating TLS are

  pthread_key_t   key

  pthread_key_create()

  pthread_setspecific()

  pthread_getspecific()

```

# **File Related Q & A**

Q.  What are holes in Files?

A.  A hole in a file area  are represented by '0'.   Holes are created when user writes data beyond the length of the file (beyond file size). The space between new data and old file size data will be filled with zero's and are called Holes.

Q.  Below question asked by one of the student.

I've written a simple program to get the current offset. It always prints '0', as if the offset is per process. I've open the log.txt in vim and was changing the cursor and was also adding the new symbols. Do you know what I'm missing here?

**offset1.c**

1. #include <sys/types.h>
2. #include <sys/stat.h>
3. #include <fcntl.h>
4. #include <unistd.h>
5. #include <stdio.h>
6. #include <stdlib.h>
7. 
8. int main()
9. {
10. printf("\noffset1 sleeping\n");
11. sleep(3);
12. 
13. ssize_t fd = open("log.txt", O_RDWR);
14. 
15. off_t offset;
16. offset = lseek(fd, 0, SEEK_CUR);
17. if (offset == (off_t)-1)
18. {
19. perror("lseek");
20. exit(1);
21. }
22. 
23. printf("\noffset1 finished: (%ld)\n", offset);
24. printf("\noffset1 current position: (%ld)\n", offset);
25. }

**offset2.c**

1. #include <sys/types.h>
2. #include <sys/stat.h>
3. #include <fcntl.h>
4. #include <unistd.h>
5. #include <stdio.h>
6. #include <stdlib.h>
7. 
8. int main()
9. {
10. ssize_t fd = open("log.txt", O_RDWR);
11. 
12. off_t offset;
13. offset = lseek(fd, 10, SEEK_SET);
14. if (offset == (off_t)-1)
15. {
16. perror("lseek");
17. exit(1);
18. }
19. 
20. printf("\noffset2 current position: (%ld)\n", offset);
21. printf("\noffset2 sleeping\n");
22. 
23. sleep(3);
24. printf("\noffset2 finished\n");
25. }

**Below output recorded after running both above programs simultaneoulsy**

offset1 sleeping

offset2 current position: (10)

offset2 sleeping

offset1 finished: (0)

offset1 current position: (0)

offset2 finished

Explanation:

**Yes the Offset works on Per process basis**, Refer to Lecture 17 and 18.

1. Here the 2 programs acts as 2 separate process.

2. Each Process will have dedicated file descriptor table.

3. There is one system wide 'open file table'.

4. Now when each process open same file, each process has entry in its own 'file descriptor table'

**5. And each process creates its own entry in 'open file table'**. Hence Offset, mode in which file is opened is specific to each Process. (**Say row1 in open file table has entry for process 1, row2 in open file table has entry for process 2, finally the inode pointer of both entries will point to same inode table**)

[FileWithHole.odp](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6f53ed4e-1fb7-4989-abd8-2d9f5dcfb16c/FileWithHole.odp)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ad274225-6f4b-49fd-972e-9d932386fce6/Untitled.png)

# **Process related Q & A**

Q . What is a 'Nice' Value?

A. Every process has its own priority. by default its value is '0', this value varies from -20 to +19.

-20 is highest priority, +19 is lowest priority.

Q. How to check the 'Nice' value of a process?

A.  'Nice' value can be found using ps, top, htop command. 'NI' column represents the Niceness value

eg:  run 'htop' on terminal, the value under column 'NI' gives nice value of the given process

Q. How to run a process(say proc1) with a given nice value? ex: run a process with nice value = -5

A. nice --5 ./proc1

Explanation to set nice value run

nice -(nice value) program_name

Q. How to run a process(say proc1) with a given nice value? ex: run a process with nice value = +10

A. nice -10 ./proc1

Q. How to change nice value of running process(with PID say 3212)? eg say a process(with PID 3212) is running with nice value = +5, now change the process nice value to -2

A. Use renice command shown below

renice -n 5 -p 3212

Q. Which scheduling Algorithm is used for Process scheduling in Linux?

A.  Completely Fair Scheduler(CFS) is used as default scheduling Algorithm.

Q. What is a Time slice in OS?

A.  The amount of time which a scheduler gives for a process to run on the Processor(CPU) is called time slice.

Q. Name few scheduling Algorithm?

A. First come first serve,  priority based scheduler, Shortest remaining time, Round Robin, CFS

# **Signals Related Q & A**

Q. What is blocking a signal ?

A. Blocking a signal means telling the Linux OS to hold the signal and  deliver it later when signal is Unblocked.

Q. How to block a signal?

A. sigprocmask() is used to 'BLOCK' and 'UNBLOCK' using the first parameter SIG_BLOCK or SIG_UNBLOCK respectively.

Q. can all signals in linux be ignored?

A. No. There are few signals that cannot be ignored ex: SIGKILL.

Q. How to generate SIGALRM signal?

A. alarm() system call generates SIGALRM signal.

Q. what are condition variables?

A. Condition variables along with mutex,  are used to signal the changes from one thread to other thread.

pthread_cond_signal() used in one thread and pthread_cond_wait() used in other waiting thread to implement above.
