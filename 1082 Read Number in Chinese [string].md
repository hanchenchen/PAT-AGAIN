# **1082** **Read Number in Chinese** [string]

1. `101000`：`yi Shi Wan yi Qian` （中间没有零）

2. `0` :`ling`

3. `100100`：`yi Shi Wan ling yi Bai`

   ```c++
   #include<iostream>
   #include<vector>
   #include<algorithm>
   using namespace std;
   vector<string> ans;
   string digit[10]={"ling","yi","er","san","si","wu","liu","qi","ba","jiu"};
   string v[10]={"","Shi","Bai","Qian","Wan","Shi","Bai","Qian","Yi"};
   int main(){
       int n,sign=0,afterzero=1;
       cin>>n;
       if(n<0){
           sign=1;
           n=-n;
       }else if(n==0){
           printf("ling");
           return 0;
       }
       for(int i=0;i<9&&n>0;i++){
           if(i==4&&n%10000!=0){
               afterzero=1;
               ans.insert(ans.begin(),v[i]);
           }
           if(n%10!=0){
               if(i!=4)ans.insert(ans.begin(),v[i]);
               ans.insert(ans.begin(),digit[n%10]);
               afterzero=0;
           }else{
               if(!ans.empty()&&*ans.begin()!="ling"&&!afterzero){
                   ans.insert(ans.begin(),digit[0]);
                   afterzero=1;
               }
           }
           n/=10;
       }
       if(sign)ans.insert(ans.begin(),"Fu");
       for(int i=0;i<ans.size();i++){
           if(ans[i]!=""){
               if(i!=0)cout<<" ";
               cout<<ans[i];
           }
       }
       return 0;
   }
   ```

   