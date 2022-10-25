#FUNÇÃO PRIMOANTERIOR#
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#FUNÇÃO PRIMO ANTERIOR#

#define tamanho_crivo 10000

int main()
{
    int num, i, j, resp=0;

    // Monta o vetor para determinar se um número é primo ou não
    char crivo[tamanho_crivo];
    memset(crivo, 1, tamanho_crivo);
    crivo[0] = 0;
    crivo[1] = 0;
    for(i=2; i < tamanho_crivo; i++){
        if(crivo[i] == 1)
            for(j=2*i; j < tamanho_crivo; j = j+i)
                crivo[j] = 0;  // Números que não são primos, pois são divisíveis por i 
    }

    printf("Digite um numero inteiro positivo:\n");
    scanf("%i", &num);

    for(i=num; i > 1; i--)
        if(crivo[i]){
            resp = i;
            break;
        }

    // Imprime os resultados
    if(resp==0)
        printf("Nao tem numero primo anterior\n");
    else
        printf("%d e o maior numero primo antes de %d\n", resp, num);

    return 0;
}
