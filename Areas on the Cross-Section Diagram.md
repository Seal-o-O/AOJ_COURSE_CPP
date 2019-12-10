## Areas on the Cross-Section Diagram

```c++
#include<iostream>
#include<stack>
#include<string>
#include<vector>
#include<algorithm>
using namespace std;

int main() {
	stack<int> S1;
	stack<pair<int, int> > S2;
	char ch;
	int sum = 0;
	for (int i = 0; cin >> ch; i++) {
		if (ch == '\\') S1.push(i);
		else if (ch == '/'&& S1.size() > 0) {
			int j = S1.top(); S1.pop();
			sum += i - j;
			int a = i - j;
			while (S2.size() > 0 && S2.top().first > j) {
				a += S2.top().second; S2.pop();
			}
			S2.push(make_pair(j, a));
		}
	}

	vector<int> ans;
	while (S2.size() > 0) {
		ans.push_back(S2.top().second);
		S2.pop();
	}
	reverse(ans.begin(), ans.end());
	cout << sum << endl;
	cout << ans.size();
	for (int i = 0; i < ans.size(); i++) {
		cout << " ";
		cout << ans[i];
	}
	cout << endl;
	getchar();
	return 0;
}
```

```
//procedure "\\//"
i=1:
	s1.push(1)	s1=[1]
i=2:
	s1.push(2)	s1=[1,2]	size=2
i=3:
	j=s1.top=2	s1.pop(2)	s1=[1]
	sum=0+(3-2)=1	a=3-2=1
	s2.push[(2,1)]	s2.size=1
i=4:
	j=s1.top=1	s1.pop(1)=1	s1.size=0
	sum=1+(4-1)=4	a=4-1=3
	a=3+1=4	s2.pop=(2,1)
	s2.push(1,4)

Vector<ans> ans:
	ans.push_back(4)	s2.pop[(1,4)]
	ans=(4)
	sum=4	ans.size=1	ans[0]=1
	cout = 4
	cout = 1 4  //done
```

