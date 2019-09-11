# 1077 **Kuchiguse**

```c++
//#include<bits/stdc++.h>
#include<iostream>
#include<string>
using namespace std;
int main(){
    int n,mini=INT_MAX;
    cin>>n;
    getchar();
    string arr[n];
    for(int i=0;i<n;i++){
        getline(cin,arr[i]);
        reverse(arr[i].begin(),arr[i].end());
        mini=min(mini,(int)arr[i].size());
    }
    int j=0;
    for(;j<mini;j++){
        int flag=0;
        for(int i=1;i<n;i++){
            if(arr[i][j]!=arr[i-1][j]){
                flag=1;
                break;
            }
        }
        if(flag)break;
    }
    if(j==0){
        cout<<"nai"<<endl;
        return 0;
    }
    string ans=arr[0].substr(0,j);
    reverse(ans.begin(),ans.end());
    cout<<ans<<endl;
}
```

