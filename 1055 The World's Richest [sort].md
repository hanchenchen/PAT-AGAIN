# **1055** **The World's Richest** [sort]

1. `N<=100000`，`age<=200`,

   每个年龄平均有500人，而题中只要求输出最多100，所以测试点二就是要求只存每个年龄的前一百个

```c++
#include<bits/stdc++.h>
#include<iostream>
#include<vector>
using namespace std;
struct NODE{
    string name;
    int age,set;
    NODE(string s,int a,int b){
        this->name=s;
        this->age=a;
        this->set=b;
    }
    bool operator <(const NODE &b)const{
            if(this->set!=b.set)return this->set>b.set;
            if(this->age!=b.age)return this->age<b.age;
            return this->name<b.name;
    }
};
vector<NODE> v_temp,v;
int main(){
    int n,k;
    cin>>n>>k;
    string s;int age,money;
    for(int i=0;i<n;i++){
        cin>>s>>age>>money;
        v_temp.push_back(NODE(s,age,money));
    }
    sort(v_temp.begin(),v_temp.end());
    int arr[201]={0};
    for(int i=0;i<v_temp.size();i++){
        if(arr[v_temp[i].age]<100){
            v.push_back(v_temp[i]);
            arr[v_temp[i].age]++;
        }
    }
    for(int i=0;i<k;i++){
        vector<NODE> ans;
        int x,y,m;
        cout<<"Case #"<<i+1<<":"<<endl;
        cin>>m>>x>>y;
        for(int i=0;i<n;i++){
            if((int)ans.size()==m)break;
            if(v[i].age>=x&&v[i].age<=y)ans.push_back(v[i]);
        }
        if(ans.size()==0){
            cout<<"None"<<endl;
            continue;
        }
        for(int j=0;j<min(m,(int)ans.size());j++){
            cout<<ans[j].name<<" "<<ans[j].age<<" "<<ans[j].set<<endl;
        }
    }
}
```

