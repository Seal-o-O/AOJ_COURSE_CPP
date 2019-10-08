```c++
#include<iostream>
#include<string>
using namespace std;

int main(){
    string w,t;
    cin>>w;
    int count=0;
    for(int i=0;i<w.size();i++){
        if(w[i]>='A'&&w[i]<='Z') w[i]+='a'-'A';
    }
    cin>>t;
    while(t!="END_OF_TEXT"){
        for(int i=0;i<t.size();i++){
        if(t[i]>='A'&&t[i]<='Z') t[i]+='a'-'A';
        }
        if(w==t) count++;
        cin>>t;
    }
    cout<<count<<endl;
}
```

