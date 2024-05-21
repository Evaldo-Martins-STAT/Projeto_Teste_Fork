
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Modelo Para Usar Controle de Version (Clonar e/ou Bifurcar (Fork)) de Projetos

<!-- badges: start -->
<!-- badges: end -->

O Objetivo do projeto Projeto_Teste_Fork é fornecer informações
necessários para usuários inciais e intermediários aprenderem a usar o
Git/Github na interface RStudio para usar Controle de Versão de
Projetos.

# Instruções de uso inicias

1.  Crie uma conta gratuita no GitHub <https://github.com/>

2.  Download o Git neste link <https://git-scm.com/downloads>

3.  Instale o git e depois abra-o. Feche e reinicie o Rstudio para
    reconhecer o local de instalção

4.  Configurando via Rstudio

    Instale o pacote `usethis` e carregue-o

``` r
library(usethis)
```

# Configure o Git/Github no RStudio

5.  Vamos usar o pacote `usethis` e os comando abaixo.

``` r
usethis::use_git_config(user.name = "Evaldo Martins", 
                        user.email = "evaldomartins@ufpa.br")
```

6.  Criar um novo token ou regenerar o token (codigo de 40 dig serão
    produzido)

``` r
usethis::create_github_token() # Muda para o site do github para fazer login
```

Depois que fizer login, gere o token na própria página do github e o
copie. Após copiar, Você deverá colocar esse número no arquivo
.Renviron. O .Renviron é um arquivo de configuração do R que permite que
você especifique variáveis de ambiente para que fiquem disponíveis para
o R. Ele é muito usado para disponibilizar senhas, chaves de API, etc. -
coisas que são secretas - e por isso não é boa prática colocá-las no
código.

7.  **Abra o o arquivo .Renviron**

``` r
usethis::edit_r_environ()
```

8.  Crie uma nova linha nesse arquivo digitando primeiramente :
    GITHUB_PAT=SEU_TOKEN. Exemplo:

GITHUB_PAT=ghp_Ko3mdlNJpBzQ7lvzKTvGFg91f6HpBQlablalba

9)  Após adicionar o token copiado do site, pule uma linha e salve o
    arquivo. \# 10) Reinicie o RStudio: CTRL + SHIFT + F10

# Como criar repositório

## Criando repositório primeiro no Github

1.  A forma mais eficiente é fazer via o site do Github, pois tudo fica
    configurado

2.  Clique no notão verde New

3.  Preencha conforme figura abaixo

<img src="images/clipboard-142360520.png" width="637" />

4.  Clone o repositório para que seja criado na sua máquina local

<img src="images/clipboard-3984491672.png" width="376" />

5.  Em seguida, no RStudio, você pode criar um novo Projeto com
    Versionamento indo em `File–> New projec`t e escolha a opção de
    `Version Control –> Git` e coloque a **url** do repositório e
    especifique a pasta onde será salvo o repositório.
6.  Ao fazer desta maneira, seu respositório já foi vinculada ao git do
    seu computador e, obviamente, está pareado com o Github na internet.

## Criando no seu proprio computador primeiro

Não é forma mais recomendada, mas é possível fazer assim.

``` r
usethis::create_project(path = "D:/Git/Clube_Codigo/Nome_Projeto")
usethis::use_git()    # Digite no console desse projeto para ligá-lo ao Git
usethis::use_github() # Digite no console desse projeto para levá-lo ao Github
```

Você também pode partir de um projeto já existem em seu computador e
depois usar as duas útlimas linhas de comando acima para ligá-lo ao git
e carregá-lo ao Github.

## Clonando e bifurcando um respositório (fork)

Quando queremos trabalhar em colaboração com mais uma ou duas pessoas,
podemos clonar um respositório e bifurcar esse repositório. Para isso,
utilize os comandos abaixo.

``` r
usethis::create_from_github(
  repo_spec = "https://github.com/Evaldo-Martins-STAT/Projeto_Teste_Fork",
  destdir = "D:/Git/Clube_Codigo/",
  fork = TRUE)
```

### Inclua pastas e arquivos no gitignore

Geralemente precisamos que arquivos e pastas não sejam compartilhados.
Para isso insira as pastas e arquivos no arquivo `gitignore`. Verifique
neste Projeto_Teste_Fork quais pastas e arquivos não são compartilhados.

# Contribuindo com o Projeto de Análise

Após ter criado um repositório a partir do Github e com a opção de fork
(Bifurcamento), você querer melhorar ainda mais o código desse projeto
de análise. Siga os passo abaixo para inserir as suas linhas de código,
seja em arquivos \*.R, \*.Rmd, \*.qmd, \*.csv, \*xlsx, ou quais outros
arquivos editáveis, ou inserir outros não editáveis dentro do projeto.
Siga os procedimentos abaixo:

1.  **Sempre** crie uma ramificação (**branch**) - A criação de branch é
    recomendada antes de mecher em qualquer arquivo do projeto. É
    importante você está na branch principal (main ou master) e use o
    comando abaixo no consolo e colocando o nome que deseja como branch.

``` r
pr_init(branch = "ajuda_grafico1")
```

2.  Agora você pode começar a fazer as contribuições nos arquivos
    desejados ou mesmo criar novos arquivos e pastas. Vamos fazer sua
    contribuição incluindo seu nome e e-mail no arquivo Readme.Rmd
    (Tabela abaixo). Depois renderize (aperte no botão Knit)

3.  Após términos das suas alterações, realize o commit (na aba git) e
    NÃO o PUSH, o qual deve ser feito via a função
    **`usethis::pr_push()`** no console e dê enter.

    ``` r
    usethis::pr_push()
    ```

4.  A página do Github se abrirá para que você possa completar o
    `Pull Request (PR)`

5.  Então comente as mudanças as mudanças que fez e clique em Criar
    Requerimento Pull (Create Pull Request)

6.  Aguarde o mantenedor do projeto fazer a mesclagem (Merge). Após a
    mesclagem, aparecerá o botão Merged (Ou Mesclado). Só então você
    finalizar sua contribuição, fechando a brunch no Rstudio

7.  A mesclagem, a qual é feita pelo mantenedor do projeto, pode ser
    feita pelo Github. Após mescalar, mantenedor pode inclusive fazer
    alterações nas suas próprias e fazer um novo commit

8.  Por sua vez, quando receber um aviso do mantenedor que foi aceita a
    sua contribuição, volte para a branch `master` , **clique primeiro**
    no botão `Pull` da aba git para atualizar as contribuições suas e
    que eventualemente o mantenedor do repositório acrescentou.

9.  Delete a branch que você criou indo primeiro para essa branch e
    digitando no console **usethis::pr_finish().**

    ``` r
    usethis::pr_finish()
    ```

10. Pronto, você está com a versão mais atualizada na sua brach
    principal (master)

11. Como boa prática, sempre comunique o mantenedor de suas
    modificaçãoes.

| \#  |          Nome           |        e-mail         |
|:---:|:-----------------------:|:---------------------:|
|  1  | Evaldo Martins da Silva | evaldomartins@ufpa.br |
|  2  |                         |                       |
|  3  |                         |                       |
|  4  |                         |                       |
|  5  |                         |                       |
|  6  |                         |                       |
|  7  |                         |                       |

Lista de Colaboradores do ProjetoRepositório

# Revertendo mudanças

Caso aconteça algum erro, é possível voltar a momento anterior às
modificações. Mas primeiro vamos ver o histórico de atualizações. Vamos
trabalhar de agora em diante nesta parte pelo terminal. Esta parte de
rever mudanças pode não ser necessárias, pois usamos poucoas linahs de
códigos. Mesmo assim, vamos ver alguns funções básicas , caso preccise.

## Como verificar o histórico de atualizações

Certifique-se de que vc está no diretório do proejto, digitando
`getwd()` no console. Agora vamos ver o histórico de comando. Digite no
terminal:

`git reflog`

## Criação de Branches e Commits

Verifica as suas branches como o comando

`git branch`

Aparecerão as branches e aquela onde stá será destacada em verde.

Vamos agora criar uma nova branch em que trabalharei no arquivo de texto
mais simples para aprendermos

`git branch textos`

## **Considerações Finais**

- **Reverter um commit:** Mantém o histórico do commit original e
  adiciona um novo commit que desfaz as mudanças.

- **Resetar para um estado anterior:** Reescreve a história do
  repositório, removendo commits subsequentes.

# Mais informações

**Mais informações neste vídeo:**

[Curso de Git e Github COMPLETO 2023 \[Iniciantes\] + Desafios + Muita
Prática](https://www.youtube.com/watch?v=kB5e-gTAl_s&t=539s)

[Curso gratuito Git e Github \#7 - Desfazendo
commit](https://www.youtube.com/watch?v=CAlg29rF2VY)  

**E nesta série Riffomonas (Code Club):**

[How to set up git for a bioinformatics project: using version control
with git and GitHub](https://www.youtube.com/watch?v=DnwEaa5QtpI)

[Integrating RStudio with a new or existing project on GitHub
(CC120)](https://www.youtube.com/watch?v=sxErFMF7BJY&list=PLmNrK_nkqBpJtNdQBPhPWjIFRYeFOGfJ1&index=10)

[Easy ways to go back in your git commit history with RStudio
(CC153)](https://www.youtube.com/watch?v=Y9h-1u6uQ6c&list=PLmNrK_nkqBpJtNdQBPhPWjIFRYeFOGfJ1&index=7)

# Anexo de criação do arquivo Readme.rmd

Para criar o Readme.rmd usei a função `usethis::use_readme_rmd()` . O
que é especial sobre usar o `README.Rmd` em vez de apenas o `README.md`?
Você pode incluir chunks como este:

``` r
summary(cars)
#>      speed           dist       
#>  Min.   : 4.0   Min.   :  2.00  
#>  1st Qu.:12.0   1st Qu.: 26.00  
#>  Median :15.0   Median : 36.00  
#>  Mean   :15.4   Mean   : 42.98  
#>  3rd Qu.:19.0   3rd Qu.: 56.00  
#>  Max.   :25.0   Max.   :120.00
```

Você ainda precisará renderizar `README.Rmd` regularmente, para manter
`README.md` atualizado.

Você também pode incorporar gráficos, por exemplo:

![](README_files/figure-gfm/pressure-1.png)<!-- -->

Nesse caso, não se esqueça de fazer o commit e enviar (push) os arquivos
de figura resultantes para que eles sejam exibidos no GitHub.
