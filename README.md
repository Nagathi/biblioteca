#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
#include <string.h>

int i = 0;
int op;
char pesquisa[100];
int verifica;
int situacao[100];
int cont = 0;

struct cadastro_livro{

    char titulo[50];
    char autor[50];
    char isbn[50];
    int ano;
    char editora[50];

    };

    struct cadastro_livro livro[100];

void inicializarBiblioteca(){
	for(i = 0; i < 100; i++){
	    *livro[i].titulo = NULL;
	    *livro[i].autor = NULL;
	    *livro[i].isbn = NULL;
	    livro[i].ano = NULL;
	    *livro[i].editora = NULL;
	}
}

void cadastrarLivro(){
	
	i = cont;
    printf("\n-------------------------------Cadastro de Livro-------------------------------\n\n\n");

    printf("Digite o título do livro: \n");
    scanf(" %[^\n]s", &livro[i].titulo);

    printf("Digite o autor do livro: \n");
    scanf(" %[^\n]s", &livro[i].autor);

    printf("Digite o código ISBN do livro: \n");
    scanf(" %[^\n]s", &livro[i].isbn);

    printf("Digite o ano do livro: \n");
    scanf(" %d", &livro[i].ano);

    printf("Digite a editora do livro: \n");
    scanf(" %[^\n]s", &livro[i].editora);
    situacao[i] = 2;
    i++;
    cont = i;	
	
}

void procurarLivro(){
	
	printf("\nDigite o título do livro que deseja procurar: ");
    scanf(" %s", &pesquisa);
    printf("\n\n");

    for(i = 0; i < 100; i++){
        if(strcmp(livro[i].titulo, pesquisa)==0){
            printf("Título: %s, ",livro[i].titulo);
            printf("Autor: %s, ",livro[i].autor);
            printf("ISBN: %s, ",livro[i].isbn);
            printf("Ano: %d, ",livro[i].ano);
            printf("Editora: %s \n\n",livro[i].editora);

            printf("O livro está na posição %d da livraria\n\n", i);
            verifica = 1;
        }
    }
    if(verifica==1){

    }else{
        printf("O livro não foi encontrado\n\n");
    }
}

void removerLivro(){
	
	printf("\nDigite o título do livro que deseja remover da livraria: ");
    scanf(" %s", &pesquisa);
    printf("\n\n");

	for(i = 0; i < 100; i++){
        if(strcmp(livro[i].titulo, pesquisa)==0){

            printf("O livro está na posição %d da livraria\n", i);

            printf("Título: %s, ",livro[i].titulo);
            printf("Autor: %s, ",livro[i].autor);
            printf("ISBN: %s, ",livro[i].isbn);
            printf("Ano: %d, ",livro[i].ano);
            printf("Editora: %s \n\n",livro[i].editora);

            situacao[i] = 0;

            *livro[i].titulo = NULL;
            *livro[i].autor = NULL;
            *livro[i].isbn = NULL;
            livro[i].ano = NULL;
            *livro[i].editora = NULL;


            printf("O livro foi removido\n\n", i);

        }
    }
	
}

void emprestarLivro(){
	
	printf("\nDigite o título do livro que deseja emprestar: ");
    scanf(" %s", &pesquisa);
    printf("\n\n");

    for(i = 0; i < 100; i++){
        if(strcmp(livro[i].titulo, pesquisa)==0){
            printf("Título: %s, ",livro[i].titulo);
            printf("Autor: %s, ",livro[i].autor);
            printf("ISBN: %s, ",livro[i].isbn);
            printf("Ano: %d, ",livro[i].ano);
            printf("Editora: %s \n\n",livro[i].editora);

            printf("O livro está na posição %d da livraria\n\n", i);
            printf("O livro foi emprestado!\n", i);

            situacao[i] = 35;
            verifica = 1;
        }
    }
    if(verifica==1){}
    else{
        printf("O livro não foi encontrado\n\n");
    }
    
}

void devolverLivro(){
	printf("\nDigite o título do livro que deseja devolver: ");
    scanf(" %s", &pesquisa);
    printf("\n\n");

    for(i = 0; i < 100; i++){
        if(strcmp(livro[i].titulo, pesquisa)==0){
            printf("Título: %s, ",livro[i].titulo);
            printf("Autor: %s, ",livro[i].autor);
            printf("ISBN: %s, ",livro[i].isbn);
            printf("Ano: %d, ",livro[i].ano);
            printf("Editora: %s \n\n",livro[i].editora);

            printf("O livro está na posição %d da livraria\n\n", i);
            printf("O livro foi devolvido!\n", i);
            situacao[i] = 2;
        }
    }
}

void listarLivrosEmprestados(){
	
	printf("\n\n\n-------------------------------Listando Livros Emprestados-------------------------------\n\n\n");

    for(i = 0; i < 100; i++){
        if(situacao[i] == 35){

            printf("Nome do Livro: %s\n", livro[i].titulo);

            printf("Nome do Autor: %s\n", livro[i].autor);

            printf("Nome do Código ISBN: %s\n", livro[i].isbn);

            printf("Ano do Livro: %d\n", livro[i].ano);

            printf("Nome da Editora: %s\n", livro[i].editora);
            
            printf("\n---------------------------------------------------------------------------------\n");
        }
    }
	
}

void listarLivrosDisponiveis(){
	
	printf("\n\n\n-------------------------------Listando Livros Disponíveis-------------------------------\n\n\n");

    for(i = 0; i < 100; i++){

        if(situacao[i] == 2){


            printf("Nome do Livro: %s\n", livro[i].titulo);

            printf("Nome do Autor: %s\n", livro[i].autor);

            printf("Nome do Código ISBN: %s\n", livro[i].isbn);

            printf("Ano do Livro: %d\n", livro[i].ano);

            printf("Nome da Editora: %s\n", livro[i].editora);
            
            printf("\n---------------------------------------------------------------------------------\n");

        }
    }
	
}

int main()
{
    setlocale(LC_ALL, "");

    printf("\n===== Livraria =====");
    printf("\n Escolha uma opção: \n\n ");
    printf("\n 1-Cadastrar livro ");
    printf("\n 2-procurar livro ");
    printf("\n 3-Retirar livro ");
    printf("\n 4-Emprestar livro ");
    printf("\n 5-Devolver livro ");
    printf("\n 6-Listar livros emprestados ");
    printf("\n 7-Listar livros disponíveis ");
    printf("\n 0-Sair \n");
    scanf("%d",&op);

    do{


        if(op==1){
            
            cadastrarLivro();

        }
        if(op==2){

        	procurarLivro();
        	
        }

        if(op==3){

            removerLivro();
            
        }

        if(op==4){

            emprestarLivro();
            
        }

        if(op==5){
        	
            devolverLivro();
            
        }

        if(op == 6){

    		listarLivrosEmprestados();
    		
        }


        if(op == 7){

            listarLivrosDisponiveis();
            
        }


        printf("\n===== Livraria =====");
        printf("\n Escolha uma opção: \n\n ");
        printf("\n 1-Cadastrar livro ");
        printf("\n 2-procurar livro ");
        printf("\n 3-Retirar livro ");
        printf("\n 4-Emprestar livro ");
        printf("\n 5-Devolver livro ");
        printf("\n 6-Listar livros emprestados ");
        printf("\n 7-Listar livros disponíveis ");
        printf("\n 0-Sair \n");
        scanf("%d",&op);

    }while(op != 0);


    return 0;
}

