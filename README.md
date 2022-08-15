```c
// Online C compiler to run C program online
#include <stdio.h>

int main() {
    int n;
    n = 3; //N principal
    
    int numero[n];
    
    int *pn[n];

    int j;
    j = 0;
    while(j<n) { //creo el puntero de cada posicion
        numero[j] = 0;
        pn[j] = &numero[j];
        j++;
    }
    
    j = 0; //solo porque la reutilizo
    

    
    //n es el total y j es el indice actual, num es por el numero que voy de 1 a 9, pn puntero de todo el numero
    int rec(int n, int j, int num, int* pn){
        pn[j]=num;
        
        if(j==n-1){//estoy en el ultimo
            
               // while(num<10){ si quiero que sea while en lugar de recursivo en la ultima altura
    
                    int x;
                    x = 0;
                    while(x<n) { //para mostrarlo
                        printf("%d",pn[x]);
                        x++;
                    }
                    printf(" ");
                    num = num +1;
                    pn[j] = num;
                //} return 1
                
                if(num>9)  return 1; //esta y la de abajo para el bucle recursivo
                rec(n,j,num,pn);

        } else {

            if(pn[j]<9){
  
                j=j+1;
                num=num+1;
                if(rec(n,j,num,pn)==1){ //aqui es que ya a terminado en 9, cambio los numeros y vuelvo a entrar
                    //printf("piso%d valor%d ",j,pn[j]);
                    j=j-1; //corrijo mi posicion de altura ya que con el anterior ++ estaba al final
                    pn[j] = pn[j]+1; //incremento esta altula +1
                    num = pn[j]; //trapaso el nuevo numero mínimo por el que empieza el bucle hasta 9
                    //printf("p%d v%d ",j,pn[j]);
                    rec(n,j,num,pn);
                    
                }

               }
            //printf(" - ");
        }
        
        return 1; //este nivel a acabado y sube al anterior
    }
    
    rec(n,j,0,numero);
    
    
    return 0;
}

```
