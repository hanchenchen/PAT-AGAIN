# **A1061** **Dating** [string]

```c++
#include<iostream>
#include<string.h>
using namespace std;
int main(){
    char str[4][100] ;
    char week[7][5]={"MON","TUE","WED","THU","FRI","SAT","SUN"};
    for(int i=0;i<4;i++){
        scanf("%s",str[i]);
    }
    int i=0;
    for(;i<min(strlen(str[0]),strlen(str[1]));i++){
        if(str[0][i]!=str[1][i])continue;
        int x=-1;
        //if(str[0][i]>='0'&&str[0][i]<='9')x=str[0][i]-'0';
        if(str[0][i]>='A'&&str[0][i]<='G')x=str[0][i]-'A';
        if(x!=-1){
            printf("%s",week[x]);
            i++;
            break;
        }
    }
    for(;i<min(strlen(str[0]),strlen(str[1]));i++){
        if(str[0][i]!=str[1][i])continue;
        int x=-1;
        if(str[0][i]>='0'&&str[0][i]<='9')x=str[0][i]-'0';
        if(str[0][i]>='A'&&str[0][i]<='N')x=str[0][i]-'A'+10;
        if(x!=-1){
            printf(" %02d",x);
            break;
        }
    }
    for(i=0;i<min(strlen(str[2]),strlen(str[3]));i++){
        if(str[2][i]!=str[3][i])continue;
        if((str[2][i]>='a'&&str[2][i]<='z')||(str[2][i]>='A'&&str[2][i]<='Z')){
            printf(":%02d\n",i);
            break;
        }
    }
    return 0;
}
```

