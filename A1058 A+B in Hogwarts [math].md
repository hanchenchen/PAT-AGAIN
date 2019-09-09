# A1058 A+B in Hogwarts [math]

```c++
#include<iostream>
using namespace std;
int main(){
    int aGalleon,bGalleon,aSickle,bSickle,aKnut,bKnut;
    scanf("%d.%d.%d",&aGalleon,&aSickle,&aKnut);
    scanf("%d.%d.%d",&bGalleon,&bSickle,&bKnut);
    int Knut=aKnut+bKnut;
    int Sickle=Knut/29+aSickle+bSickle;
    int Galleon=Sickle/17+aGalleon+bGalleon;
    printf("%d.%d.%d",Galleon,Sickle%17,Knut%29);
    return 0;
}
```

