# Caixa-de-supermarcado
# Caixa de Supermercado
Nosso trabalho será um simulador de caixa de supermercado, como Bahamas, onde o funcionário poderá realizar cadastro de mercadoria, com nome, código, quantidade, preço, consultar estoque, modificar estoque, modificar o preço da mercadoria, fazer o controle de caixa como caixa atual, consular caixa e realizar a venda para o cliente.

Projeto_Caixa_de_Supermercado
Nome do campo|	tipo |	Descrição|
|------------|-------|-----------|
|cadastrar |	inteiro |	Constará no menu de opçoes e fará o cadastro de um novo produto |
alterarEstoque |	inteiro |	Constará no menu e alterará a quantidade em estoque |
| modificarPreco | 	Real	| Constará no menu e modificará o preço do produto |
|venda |	Real | Constará no menu e mostrará o valor total de venda |
|listaProduto	| inteiro |	Constará no menu e mostrará os produtos no estoque |
consultarSaldo |	Real	 | Constará no menu e mostrará o valor existente no caixa |
codigo	| Inteiro	 | Código do produto |
nome	| Cadeia de caracteres	|Nome do produto |
|quantidade	| Inteiro |	Quantidade de produtos |
|preco |	Real	| Valor do produto |
caixaAtual |	Real	| Valor disponivel no caixa|


Grupo:

ADRIELY AVELINO DE CASTRO

EMERSON SOUZA DA SILVA

SAULO FURTADO NUNES

#include<stdio.h>
#include<stdlib.h>
#include<locale.h>

/*
Equique: Saulo F Nunes, Adriely , Emerson
Disciplina: Linguagem de programacão 1

 */

//CONSTANTE PARA CONTROLAR QUANTIDADE DE DADOS
#define QTREG 30


//ESTRUTURA UTILIZADA PARA CADASTRAR PRODUTOS

typedef struct {
    int codigo;
    char nome[30];
    int quantidade;
    float preco;
} REGPRODUTO;

//CRIA VARIAVEL DO TIPO regproduto
REGPRODUTO produto[QTREG];

//VARIAVEIS GLOBAIS
float caixaAtual = 800.00;

//CABEÇALHO DAS FUNÇÕES QUE SERÃO USADAS

//CABEÇALHO DA FUNÇÃO INSERIR UM PRODUTO NO ESTOQUE
int cadastrar();

//CABEÇALHO DA FUNÇÃO AUMENTAR O ESTOQUE DE UM PRODUTO
void alterarEstoque(int pCodgio, int pQuantidade);

//CABEÇALHO DA FUNÇÃO MODIFICAR O PREÇO DE UM PRODUTO
void modificarPreco(int pCodigo, float pPreco);

//CABEÇALHO DA FUNÇÃO REALIZAR VENDA
float venda();

//CABEÇALHO DA FUNÇÃO CONSULTAR O ESTOQUE DOS PRODUTOS
void listaProduto(int pQtProduto);

//CABEÇALHO DA FUNÇÃO CONSULTAR O SALDO DO CAIXA
void consultarSaldo();

int main(void) {

    int op = 0;

    setlocale(LC_ALL, "Portuguese");

    while (op != 7) {
        printf("\n\n\t* Aividade Prof Joventino - Equipe Saulo, Adriely e Emerson *\n\n\n");
        printf("\n\n\t*  Super Mercado - Sistema de gerenciamento de mercadoria 2020 *\n\n\n");
        printf("MENU\n\n1 - Cadastrar Produto\n2 - Atualizar Estoque\n3 - Alterar preco produto");
        printf("\n4 - Realizar venda\n5 - Consultar estoque\n6 - Consultar saldo do caixa\n7 - Sair\n");
        fflush(stdout);
        scanf("%d", &op);
        fflush(stdin);
        system("cls");

        switch (op) {
            int qtProduto;
            float lucro;
            case 1://OPÇÃO CADASTRAR PRODUTO
                qtProduto = cadastrar();
                break;
            case 2:
            {//OPÇÃO ATUALIZAR ESTOQUE
                int pCodigo, pQuantidade;
                printf("Digite o código do produto que deseja atualizar o estoque:");
                fflush(stdout);
                scanf("%d", &pCodigo);
                fflush(stdin);
                printf("Deseja alterar quantidade do produto: %s - quantidade: %d \n", produto[pCodigo].nome, produto[pCodigo].quantidade);
                printf("Nova quantidade:");
                fflush(stdout);
                scanf("%d", &pQuantidade);
                fflush(stdin);
                system("pause");
                alterarEstoque(pCodigo, pQuantidade);
            }
                break;
            case 3:
            {//OPÇÃO ALTERAR PREÇO DO PRODUTO
                int pCodigo;
                float pPreco;
                printf("Digite o código do produto que deseja modificar o preco:");
                fflush(stdout);
                scanf("%d", &pCodigo);
                fflush(stdin);
                printf("Deseja modificar o preco do produto: %s - preco: %0.2f \n", produto[pCodigo].nome, produto[pCodigo].preco);
                printf("Novo preco:");
                fflush(stdout);
                scanf("%f", &pPreco);
                fflush(stdin);
                system("pause");
                modificarPreco(pCodigo, pPreco);
            }
                break;
            case 4://OPÇÃO DE REALIZAR VENDA
                lucro = venda();
                caixaAtual = caixaAtual + lucro;
                break;
            case 5://OPÇÃO DE LISTAR PRODUTOS
                listaProduto(qtProduto);
                break;
            case 6://CONSULTAR SALDO NO CAIXA
                consultarSaldo();
                break;
            case 7://OPÇÃO SAIR DO PROGRAMA
                break;
            default:// EXIBI MENSAGEM DE OPÇÃO INVALIDA CASO DIGITE UM NUMERO QUE NÃO TENHA NO MENU
                printf("Opcão inválida");
                fflush(stdout);
                break;

        }
    }


    system("pause");
    return 0;

}
