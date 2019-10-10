# Insertion Sort

```c++
#include<iostream>

using namespace std;

int main(){
    int a[100]={};
    int n;
    cin>>n;
    for(int i=0; i<n; i++){
        cin>>a[i];
    }
    for(int i=0; i<n; i++){
        cout<<a[i]<<(i==n-1?'\n':' ');
    }
    for(int i=1; i<n; i++){
        int key = a[i];
        int j=i-1;
        while(j>=0&&a[j]>key){
            a[j+1]=a[j];
            j--;
        }
        a[j+1]=key;
        for(int k=0; k<n; k++){
            cout<<a[k]<<(k==n-1?'\n':' ');
        }
        
    }
    return 0;
}
```

```c++
#include<iostream>
#include<vector>
using namespace std;
int main(){
  int n;cin>>n;
  int i,j,k;
  vector<int> v;
  for(i=0;i<n;i++){
    cin >> k;
    v.push_back(k);
  }
  for(j=0;j<n;j++) cout << v[j] << (j==n-1?'\n':' ');
  for(i=1;i<n;i++){
    for(j=0;j<i;j++){
      if(v[j]>v[i]){
	k=v[i];
	v.erase(v.begin()+i);
	v.insert(v.begin()+j,k);
	break;
      }
    }
    for(j=0;j<n;j++) cout << v[j] << (j==n-1?'\n':' ');
  }
  return 0;
}
```

1 、基本操作

(1)头文件：#include<vector>.

(2)创建vector对象：vector<int> vec;

(3)尾部插入数字：vec.push_back(a);

(4)使用下标访问元素：cout<<vec[0]<<endl;记住下标是从0开始的。

(5)使用迭代器访问元素.

vector<int>::iterator it;

for(it=vec.begin();it!=vec.end();it++)

    cout<<*it<<endl;

(6)插入元素：    vec.insert(vec.begin()+i,a);在第i+1个元素前面插入a;

(7)删除元素：    vec.erase(vec.begin()+2);删除第3个元素

vec.erase(vec.begin()+i,vec.end()+j);删除区间[i,j-1];区间从0开始

(8)向量大小:vec.size();

(9)清空:vec.clear();
