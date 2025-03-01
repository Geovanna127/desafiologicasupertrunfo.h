#include <stdio.h>
#include <string.h>

// Estrutura para armazenar as informações de uma carta
typedef struct {
    char estado[50];
    char codigo[10];
    char nomeCidade[50];
    int populacao;
    float area;
    float pib;
    int pontosTuristicos;
    float densidadePopulacional;
    float pibPerCapita;
} Carta;

// Função para calcular densidade populacional
float calcularDensidadePopulacional(int populacao, float area) {
    return populacao / area;
}

// Função para calcular PIB per capita
float calcularPIBPerCapita(float pib, int populacao) {
    return pib / populacao;
}

// Função para determinar a carta vencedora com base em um atributo
void compararCartas(Carta carta1, Carta carta2, char atributo[]) {
    printf("\nComparação de cartas (Atributo: %s):\n", atributo);

    // Comparação por População (maior vence)
    if (strcmp(atributo, "Populacao") == 0) {
        printf("Carta 1 - %s (%s): %d\n", carta1.nomeCidade, carta1.estado, carta1.populacao);
        printf("Carta 2 - %s (%s): %d\n", carta2.nomeCidade, carta2.estado, carta2.populacao);

        if (carta1.populacao > carta2.populacao) {
            printf("Resultado: Carta 1 (%s) venceu!\n", carta1.nomeCidade);
        } else if (carta1.populacao < carta2.populacao) {
            printf("Resultado: Carta 2 (%s) venceu!\n", carta2.nomeCidade);
        } else {
            printf("Resultado: Empate!\n");
        }
    }

    // Comparação por Densidade Populacional (menor vence)
    else if (strcmp(atributo, "Densidade Populacional") == 0) {
        printf("Carta 1 - %s (%s): %.2f\n", carta1.nomeCidade, carta1.estado, carta1.densidadePopulacional);
        printf("Carta 2 - %s (%s): %.2f\n", carta2.nomeCidade, carta2.estado, carta2.densidadePopulacional);

        if (carta1.densidadePopulacional < carta2.densidadePopulacional) {
            printf("Resultado: Carta 1 (%s) venceu!\n", carta1.nomeCidade);
        } else if (carta1.densidadePopulacional > carta2.densidadePopulacional) {
            printf("Resultado: Carta 2 (%s) venceu!\n", carta2.nomeCidade);
        } else {
            printf("Resultado: Empate!\n");
        }
    }

    // Comparação por PIB (maior vence)
    else if (strcmp(atributo, "PIB") == 0) {
        printf("Carta 1 - %s (%s): %.2f\n", carta1.nomeCidade, carta1.estado, carta1.pib);
        printf("Carta 2 - %s (%s): %.2f\n", carta2.nomeCidade, carta2.estado, carta2.pib);

        if (carta1.pib > carta2.pib) {
            printf("Resultado: Carta 1 (%s) venceu!\n", carta1.nomeCidade);
        } else if (carta1.pib < carta2.pib) {
            printf("Resultado: Carta 2 (%s) venceu!\n", carta2.nomeCidade);
        } else {
            printf("Resultado: Empate!\n");
        }
    }

    // Comparação por PIB per capita (maior vence)
    else if (strcmp(atributo, "PIB per capita") == 0) {
        printf("Carta 1 - %s (%s): %.2f\n", carta1.nomeCidade, carta1.estado, carta1.pibPerCapita);
        printf("Carta 2 - %s (%s): %.2f\n", carta2.nomeCidade, carta2.estado, carta2.pibPerCapita);

        if (carta1.pibPerCapita > carta2.pibPerCapita) {
            printf("Resultado: Carta 1 (%s) venceu!\n", carta1.nomeCidade);
        } else if (carta1.pibPerCapita < carta2.pibPerCapita) {
            printf("Resultado: Carta 2 (%s) venceu!\n", carta2.nomeCidade);
        } else {
            printf("Resultado: Empate!\n");
        }
    }

    // Comparação por Pontos turísticos (maior vence)
    else if (strcmp(atributo, "Pontos Turisticos") == 0) {
        printf("Carta 1 - %s (%s): %d\n", carta1.nomeCidade, carta1.estado, carta1.pontosTuristicos);
        printf("Carta 2 - %s (%s): %d\n", carta2.nomeCidade, carta2.estado, carta2.pontosTuristicos);

        if (carta1.pontosTuristicos > carta2.pontosTuristicos) {
            printf("Resultado: Carta 1 (%s) venceu!\n", carta1.nomeCidade);
        } else if (carta1.pontosTuristicos < carta2.pontosTuristicos) {
            printf("Resultado: Carta 2 (%s) venceu!\n", carta2.nomeCidade);
        } else {
            printf("Resultado: Empate!\n");
        }
    }
}

// Função principal
int main() {
    // Cadastro das cartas
    Carta carta1 = {"São Paulo", "SP01", "São Paulo", 12300000, 1521.11, 700000.0, 10, 0, 0};
    Carta carta2 = {"Rio de Janeiro", "RJ01", "Rio de Janeiro", 6700000, 1200.27, 400000.0, 8, 0, 0};

    // Cálculo de densidade populacional e PIB per capita
    carta1.densidadePopulacional = calcularDensidadePopulacional(carta1.populacao, carta1.area);
    carta1.pibPerCapita = calcularPIBPerCapita(carta1.pib, carta1.populacao);

    carta2.densidadePopulacional = calcularDensidadePopulacional(carta2.populacao, carta2.area);
    carta2.pibPerCapita = calcularPIBPerCapita(carta2.pib, carta2.populacao);

    int nivel;
    char atributoEscolhido[20];

    // Seleção do nível
    printf("Escolha o nível de dificuldade:\n1. Novato\n2. Aventureiro\n3. Mestre\n");
    scanf("%d", &nivel);

    if (nivel == 1) {
        printf("\nNível Novato: Escolha o atributo para comparar (Populacao, Densidade Populacional): ");
        scanf("%s", atributoEscolhido);
        compararCartas(carta1, carta2, atributoEscolhido);
    } else if (nivel == 2) {
        printf("\nNível Aventureiro: Escolha o atributo para comparar (Populacao, Densidade Populacional, PIB, Pontos Turisticos): ");
        scanf("%s", atributoEscolhido);
        compararCartas(carta1, carta2, atributoEscolhido);
    } else if (nivel == 3) {
        printf("\nNível Mestre: Escolha o atributo para comparar (Populacao, Densidade Populacional, PIB, PIB per capita, Pontos Turisticos): ");
        scanf("%s", atributoEscolhido);
        compararCartas(carta1, carta2, atributoEscolhido);
    } else {
        printf("Nível inválido!\n");
    }

    return 0;
}
