# **1065** **A+B and C (64bit)** 

```c++
//#include<bits/stdc++.h>
#include<iostream>
using namespace std;
bool cmp(string x,string y){
    /*
    int sign_x=1,sign_y=1;
    if(!x.empty()&&x[0]=='-')sign_x=0;
    if(!y.empty()&&y[0]=='-')sign_y=0;
    if(sign_x!=sign_y)return sign_x>sign_y;
    */
  
    /*
    没有对前导零测试点
    int i=0;
    while(x[i]=='0'||x[i]=='-'||x[i]=='+')i++;
    x=x.substr(i);
    i=0;
    while(y[i]=='0'||y[i]=='-'||y[i]=='+')i++;
    y=y.substr(i);
    */
    if(x.size()!=y.size())return x.size()>y.size();
    for(int i=0;i<y.size();i++){
        if(x[i]!=y[i])return (x[i]>y[i]);//==sign_x;
    }
    return false;
}
string add(string x,string y){
    reverse(x.begin(),x.end());reverse(y.begin(),y.end());
    if(x.size()<y.size())swap(x,y);
    int c=0,a,i=0;
    for(;i<y.size();i++){
        a=x[i]+y[i]-'0'-'0'+c;
        c=a/10;
        a%=10;
        x[i]=a+'0';
    }
    if(i<x.size())x[i]+=c;
    else if(c)x+="1";
    reverse(x.begin(),x.end());
    cout<<x<<endl;
    return x;
}
int main(){
    int n;cin>>n;
    for(int i=1;i<=n;i++){
        string a,b,c;
        bool ans;
        cin>>a>>b>>c;
        if(a[0]=='-'){
            if(b[0]=='-'){
                if(c[0]=='-'){
                    ans=!cmp(add(a.substr(1),b.substr(1)),c.substr(1));
                }else{
                    ans=false;
                }
            }else{
                if(c[0]=='-'){
                    ans=cmp(add(c.substr(1),b),a.substr(1));
                }else{
                    ans=!cmp(add(c,a.substr(1)),b);
                }
            }
        }else{
            if(b[0]=='-'){
                if(c[0]=='-'){
                    ans=cmp(add(a,c.substr(1)),b.substr(1));
                }else{
                    //cout<<i<<endl;
                    ans=!cmp(add(b.substr(1),c),a);
                }
            }else{
                if(c[0]=='-'){
                    ans=cmp(add(b,a),c);
                }else{
                    ans=cmp(add(b,a),c);
                }
            }
            
        }
        printf("Case #%d: %s\n",i,ans?"true":"false");
    }
    return 0;
}
```

