#include <iostream>

class drob{
  public:
    int celoe;
    int chislitel;
    int znamenatel;

    drob(){
      celoe=0;
      chislitel=0;
      znamenatel=1;
    }
    drob(int a,int b,int c){
      celoe=a;
      chislitel=b;
      znamenatel=c;
    }

    void plys(drob a){
      celoe+=a.celoe;
      chislitel=chislitel*a.znamenatel+a.chislitel*znamenatel;
      znamenatel*=a.znamenatel;
      
      celoe=chislitel/znamenatel;
      chislitel=chislitel%znamenatel;
      
      for(int i=chislitel;i>=0;i--){
        if(chislitel%i==0&& znamenatel%i==0){
          chislitel/=i;
          znamenatel/=i;
        }
      }
      
      if(chislitel==0){
        znamenatel=1;
      }
    }

    void minys(drob a){
      chislitel=(chislitel*a.znamenatel+celoe*znamenatel)-(a.chislitel*znamenatel+a.celoe*a.znamenatel);
      znamenatel*=a.znamenatel;
      
      celoe=chislitel/znamenatel;
      chislitel=chislitel%znamenatel;
      
      for(int i=chislitel;i>=0;i--){
        if(chislitel%i==0&& znamenatel%i==0){
          chislitel/=i;
          znamenatel/=i;
        }
      }
      
      if(chislitel==0){
        znamenatel=1;
      }
      
    }

    void umnojit(drob a){
      chislitel=(celoe*znamenatel+chislitel)*(a.celoe*znamenatel+chislitel);
      znamenatel*=a.znamenatel;
      
      celoe=chislitel/znamenatel;
      chislitel=chislitel%znamenatel;

      for(int i=chislitel;i>=0;i--){
        if(chislitel%i==0&& znamenatel%i==0){
          chislitel/=i;
          znamenatel/=i;
        }
      }
      
      if(chislitel==0){
        znamenatel=1;
      }
    }

    void razdelit(drob a){
      chislitel=(znamenatel*celoe+chislitel)*a.znamenatel;
      znamenatel=znamenatel*(a.celoe*a.znamenatel+a.chislitel);

      celoe=chislitel/znamenatel;
      chislitel=chislitel%znamenatel;

      for(int i=chislitel;i>=0;i--){
        if(chislitel%i==0&& znamenatel%i==0){
          chislitel/=i;
          znamenatel/=i;
        }
      }

      if(chislitel==0){
        znamenatel=1;
      }
      
    }

    void print(){
      std::cout<<celoe<<" "<<chislitel<<"/"<<znamenatel<<"\n";
    }

};

int main() {
  drob a(1,1,2);

}
