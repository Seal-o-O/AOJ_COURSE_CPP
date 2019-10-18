# Stable Sort

Let's arrange a deck of cards. There are totally 36 cards of 4 suits(S, H, C, D) and 9 values (1, 2, ... 9). For example, 'eight of heart' is represented by H8 and 'one of diamonds' is represented by D1.

Your task is to write a program which sorts a given set of cards in ascending order by their values using the Bubble Sort algorithms and the Selection Sort algorithm respectively. These algorithms should be based on the following pseudocode:

```
BubbleSort(C)
1 for i = 0 to C.length-1
2     for j = C.length-1 downto i+1
3         if C[j].value < C[j-1].value
4             swap C[j] and C[j-1]
SelectionSort(C)
1 for i = 0 to C.length-1
2     mini = i
3     for j = i to C.length-1
4         if C[j].value < C[mini].value
5             mini = j
6     swap C[i] and C[mini]
```

Note that, indices for array elements are based on 0-origin.

For each algorithm, report the stability of the output for the given input (instance). Here, 'stability of the output' means that: cards with the same value appear in the output in the same order as they do in the input (instance).



## Input

The first line contains an integer *N*, the number of cards.

*N* cards are given in the following line. Each card is represented by two characters. Two consecutive cards are separated by a space character.

## Output

In the first line, print the arranged cards provided by the Bubble Sort algorithm. Two consecutive cards should be separated by a space character.

In the second line, print the stability ("Stable" or "Not stable") of this output.

In the third line, print the arranged cards provided by the Selection Sort algorithm. Two consecutive cards should be separated by a space character.

In the fourth line, print the stability ("Stable" or "Not stable") of this output.

## Constraints

1 ≤ *N* ≤ 36

## Sample Input 1

```
5
H4 C9 S4 D2 C3
```

## Sample Output 1

```
D2 C3 H4 S4 C9
Stable
D2 C3 S4 H4 C9
Not stable
```

## Sample Input 2

```
2
S1 H1
```

## Sample Output 2

```
S1 H1
Stable
S1 H1
Stable
```

```c++
#include<bits/stdc++.h>
using namespace std;
#define int long long
signed main(){
  int n;
  cin>>n;
  string A[n];
  for(int i=0;i<n;i++) cin>>A[i];
  string C[n];
  for(int i=0;i<n;i++) C[i]=A[i];
  int ans=0;
    //C sorting by number
  for(int i=0;i<n;i++){
    for(int j=n-1;j>i;j--){
      if(C[j][1]<C[j-1][1]){
	swap(C[j],C[j-1]);
      }
    }
  }
    //+=的作用就是把重复数字前的字符+在一起，判断是否稳定（一样）
  string x[10],y[10];
  for(int i=0;i<n;i++){
    x[A[i][1]-'0']+=A[i][0];
    y[C[i][1]-'0']+=C[i][0];
  }
  ans=1;
  for(int i=0;i<10;i++) ans&=x[i]==y[i]; //ans = ans & (x[i] == y[i]),x[i] == y[i]时为1，否则为0，实则这个代码的意思就是相等时ans=1，否则为0
  for(int i=0;i<n;i++) cout<<C[i]<<" \n"[i==n-1];
  cout<<(ans?"Stable":"Not stable")<<endl;
  
  for(int i=0;i<n;i++) C[i]=A[i];
  for(int i=0;i<n;i++){
    int minj=i;
    for(int j=i;j<n;j++){
      if(C[j][1]<C[minj][1]){
	minj=j;
      }
    }
    if(i!=minj) swap(C[i],C[minj]);
  }
  
  for(int i=0;i<10;i++) x[i]=y[i]="";
  for(int i=0;i<n;i++){
    x[A[i][1]-'0']+=A[i][0];
    y[C[i][1]-'0']+=C[i][0];
  }
  ans=1;
  for(int i=0;i<10;i++) ans&=x[i]==y[i]; 
  for(int i=0;i<n;i++) cout<<C[i]<<" \n"[i==n-1];
  cout<<(ans?"Stable":"Not stable")<<endl;
  
  return 0;
}

```

![1571316530088](C:\Users\Gin\AppData\Roaming\Typora\typora-user-images\1571316530088.png)