

```
#include<iostream>
#include<string>
using namespace std;

int main(){
	string str;
    cin>>str;
    while(str[0]!='0'){
        int i,sum=0;
        for(i=0;i<str.size();i++){
            sum+=str[i]-'0';
        }
        cout<<sum<<endl;
        cin>>str;
    }
    return 0;
}

```

