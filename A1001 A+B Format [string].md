# A1001 A+B Format [string]

```c++
#include<iostream>
using namespace std;
int main(){
    int a,b;
    cin>>a>>b;
    a+=b;
    string s=to_string(a);
    int n=(int)s.size();
    for(int i=0;i<n;i++){
        cout<<s[i];
        if((n-i-1)%3==0&&i!=0&&s[i-1]!='-')cout<<",";
    }
    return 0;
}
```

