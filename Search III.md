# Search III

Your task is to write a program of a simple *dictionary* which implements the following instructions:

- **insert \*str\***: insert a string *str* in to the dictionary
- **find \*str\***: if the distionary contains *str*, then print 'yes', otherwise print 'no'

## Input

In the first line *n*, the number of instructions is given. In the following *n* lines, *n* instructions are given in the above mentioned format.

## Output

Print yes or no for each find instruction in a line.

## Constraints

- A string consists of 'A', 'C', 'G', or 'T'
- 1 ≤ length of a string ≤ 12
- *n* ≤ 1000000

## Sample Input 1

```
5
insert A
insert T
insert C
find G
find A
```

## Sample Output 1

```
no
yes
```

## Sample Input 2

```
13
insert AAA
insert AAC
insert AGA
insert AGG
insert TTT
find AAA
find CCC
find CCC
insert CCC
find CCC
insert T
find TTT
find T
```

## Sample Output 2

```
yes
no
no
yes
yes
yes
```

```c++
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define TABLE_SIZE 16777216
#define ORDER_LENGTH 7
#define STR_LENGTH 13

using namespace std;

int array[128];
//构造哈希函数
int translateStr(char buf[]){
    int sum = -1,mult = 1;
    for(int i = 0; buf[i] != '\0'; i++){
        sum += array[buf[i]]*mult;
        mult *= 4;
    }
    return sum;
}

int main(){
//把字符转换为数值，便于哈希函数转换
    array['A']=1,array['C']=2,array['G']=3,array['T']=4;

    int n;
    scanf("%d",&n);
    char order[ORDER_LENGTH],str[STR_LENGTH];

    char* check_table = new char[TABLE_SIZE];

    for(int i = 0; i < n; i++){
        scanf("%s %s",order,str);
        if(order[0] == 'i'){
            check_table[translateStr(str)] = 'Y';//若插入该值，则哈希的key为Y（存在）
        }else{
            if(check_table[translateStr(str)] == 'Y'){
                printf("yes\n");
            }else{
                printf("no\n");
            }
        }
    }
}

```

