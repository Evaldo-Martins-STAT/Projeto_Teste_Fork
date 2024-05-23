
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Modelo Para Usar Controle de Version (Clonar e/ou Bifurcar (Fork)) de Projetos

<!-- badges: start -->
<!-- badges: end -->

O Objetivo do projeto Projeto_Teste_Fork é fornecer informações
necessários para usuários inciais e intermediários aprenderem a usar o
Git/Github na interface RStudio para usar Controle de Versão de
Projetos. A primeira parte usa as funções do pacote `usethis,` e a
partir da seção *Trabalhando com Versionamento*, usamos os comandos do
Git.

# Instruções Inicias para uso do Git/Github

1.  Crie uma conta gratuita no GitHub <https://github.com/>

2.  Download o arquivo executável do Git neste link
    <https://git-scm.com/downloads>

3.  Instale o git e depois abra-o. Feche e reinicie o Rstudio para
    reconhecer o local de instalção do Git.

4.  Configurando via Rstudio

    Instale o pacote `usethis` e carregue-o

``` r
library(usethis)
```

# Configure o Git/Github no RStudio

5.  Vamos usar o pacote `usethis` e os comando abaixo para parear com a
    sua conta no Github. Acesso das de sua conta e e-mail em
    Configurações –\> Perfil Público.

``` r
usethis::use_git_config(user.name = "Evaldo Martins", 
                        user.email = "evaldomartins@ufpa.br")
```

6.  Criar um novo token ou regenerar o token (codigo de 40 dígitos serão
    produzido)

``` r
usethis::create_github_token() # Muda para o site do github para fazer login
```

Depois que fizer login, gere o token na própria página do github e o
copie. Após copiar, Você deverá colocar esse número no arquivo
`.Renviron`. O `.Renviron` é um arquivo de configuração do R que permite
que você especifique variáveis de ambiente para que fiquem disponíveis
para o R. Ele é muito usado para disponibilizar senhas, chaves de API,
etc. - coisas que são secretas - e por isso não é boa prática colocá-las
no código.

7.  **Abra o o arquivo .Renviron**

``` r
usethis::edit_r_environ()
```

8.  Crie uma nova linha nesse arquivo digitando primeiramente :
    GITHUB_PAT=SEU_TOKEN. Exemplo:

GITHUB_PAT=ghp_Ko3mdlNJpBzQ7lvzKTvGFg91f6HpBQlablalba

9)  Após adicionar o token copiado do site, pule uma linha e salve o
    arquivo.
10) Reinicie o RStudio: CTRL + SHIFT + F10

# Como criar repositório

## Criando repositório primeiro no Github

1.  A forma mais eficiente de criar repositório é fazer via o site do
    Github, pois tudo fica configurado

2.  Clique no notão verde **New**

3.  Preencha conforme figura abaixo

<img src="images/clipboard-142360520.png" width="637" />

4.  Clone o repositório para que seja criado na sua máquina local

<img src="images/clipboard-3984491672.png" width="376" />

**Baixando o repositório(Projeto):**

5.  Em seguida, no RStudio, você pode criar um novo **Projeto com
    Versionamento** indo em `File–> New projec`t e escolha a opção de
    `Version Control –> Git` e coloque a **url** do repositório e
    especifique a pasta onde este será salvo.

6.  Ao fazer desta maneira, seu respositório já fica vinculado ao git do
    seu computador e, obviamente, está pareado com o Github na internet.

    **Implemente pequenas mudanças no seu projeto:**

7.  Faça pequenos testes de alteração no seu repositório testes, como:
    *criar pasta e arquivo na pasta do projeto, comitar por meio da aba
    git, realizar push*.

8.  Verifique no servidor do Github as alterações.

9.  Faça alteração no arquivo Readme no Github web, commit e depois faça
    Pull no RStudio.

## Criando o Repositório no Computador Primeiro

Não é a forma mais recomendada, mas é possível criar um repositório
pareado com o Github no computador priemeiro da sequinte maneira:

``` r
usethis::create_project(path = "D:/Git/Clube_Codigo/Nome_Projeto")
usethis::use_git()    # Digite no console desse projeto para ligá-lo ao Git
usethis::use_github() # Digite no console desse projeto para levá-lo ao Github
```

**De um projeto existente no computador:**

Você também pode partir de um `Projeto já existem em seu computador`.
Abra o projeto e depois use as duas útlimas linhas de comando acima para
ligá-lo ao git e carregá-lo ao Github.

## Clonando e bifurcando um respositório (fork)

Quando queremos trabalhar em colaboração com mais pessoas, podemos
clonar um respositório e bifurcá-lo ao mesmo tempo. Para isso, utilize
os comandos abaixo.

``` r
usethis::create_from_github(
  repo_spec = "https://github.com/Evaldo-Martins-STAT/Projeto_Teste_Fork",
  destdir = "D:/Git/Clube_Codigo/",
  fork = TRUE)
```

## Inclua pastas e arquivos no arquivo .gitignore

Geralmente precisamos que arquivos e pastas não sejam
compartilhados/divulgados. Para isso, insira as pastas e arquivos no
arquivo .`gitignore`. Verifique neste Projeto_Teste_Fork quais pastas e
arquivos não são compartilhados.

# Contribuindo com o Projeto de Análise

Após ter criado um repositório a partir localizado no Github e com a
opção de fork (Bifurcamento), você querer melhorar ainda mais o código
desse projeto de análise. Siga os passo abaixo para inserir as suas
linhas de código, seja em arquivos `*.R`, `*.Rmd`, `*.qmd`, `*.csv`,
`*xlsx`, ou quais outros arquivos editáveis, ou inserir outros não
editáveis dentro do projeto.

1.  **Sempre** crie uma ramificação (**branch**) - A criação de branch é
    recomendada antes de alterar qualquer arquivo do projeto. É
    importante você esteja na branch principal (master) e use o comando
    abaixo no console e dando nome apropriado à branch que reflita as
    modificações que deseja implementar.

``` r
pr_init(branch = "ajuda_grafico1")
```

2.  Agora, você pode começar a fazer as contribuições nos arquivos
    desejados ou mesmo criar novos arquivos e pastas. Faça uma pequena
    modificação no arquivo Readme.Rmd (Tabela abaixo), incluindo seu
    nome e e-mail . Depois renderize (aperte no botão Knit).

3.  Após término das suas alterações, realize o `Commit` (Botão na aba
    git)

4.  NÃO pressione o botão
    <span style="color: lightgreen;">**Push**</span> agora. A operação
    de “empurrar” deve feita via digitação da função
    **`usethis::pr_push()`** no console, seguida de Enter, a fim de
    criar uma Pull Request também.

    ``` r
    usethis::pr_push()
    ```

5.  A página do Github se abrirá para que você possa completar o
    `Pull Request (PR)`

6.  Então comente as mudanças que fez e clique em
    `Criar Requerimento Pull` (ou `Create Pull Request`)

7.  Aguarde o mantenedor do projeto fazer a mesclagem (Merge). Após a
    mesclagem, aparecerá o botão Merged (Ou Mesclado). Só então você
    finaliza sua contribuição, fechando a brunch no Rstudio

    **Obs1:** Quanto ao mantenedor, a mesclagem do projeto pode ser
    feita pelo Github. Após mesclar com a branch `master`, o mantenedor
    pode inclusive fazer alterações próprias e fazer um novo commit.

8.  Por sua vez, quando receber um aviso do mantenedor de que foi aceita
    a sua contribuição, volte para a branch `master` no RStudio, e então
    **clique primeiro** no botão
    <span style="color: lightblue;">**Pull**</span> da aba git para
    atualizar as contribuições suas mescladas e outras que eventualmente
    o mantenedor do repositório acrescentou.

9.  Delete a branch que você criou, voltando a ela via aba `Git` e
    digitando no console **usethis::pr_finish().**

    ``` r
    usethis::pr_finish()
    ```

10. Pronto, você está com a versão mais atualizada na sua brach
    principal (master)

    **Obs2**: Como boa prática, sempre comunique o mantenedor de suas
    modificaçãoes.

**Cadastre seu nome e endereço de e-mail abaixo:**

| \#  |              Nome               |          e-mail           |
|:---:|:-------------------------------:|:-------------------------:|
|  1  |     Evaldo Martins da Silva     |   evaldomartins@ufpa.br   |
|  2  | Rayane Leticia Furtado Pinheiro | rayanefurtado63@gmail.com |
|  3  |                                 |                           |
|  4  |                                 |                           |
|  5  |                                 |                           |
|  6  |                                 |                           |
|  7  |                                 |                           |

Lista de Colaboradores do ProjetoRepositório

# **Trabalhando com versionamento**

De agora em diante, vamos trabalhar via Terminal do RStudio a fim de
trabalhar de forma mais profissional com versionamento.

## **Verificando o histórico de atualizações**

Certifique-se de que vc está no diretório do projeto, digitando
`getwd()` no console. Agora vamos ver o histórico de comando. Digite no
terminal:

`git reflog`

A aparecerá uma lista de todos os commits (versionamentos) que você já
fez no projeto. Vamos agora exercitar o que já fizemos com as funções do
pacote usethis e também com funções do git.

## **Criação de Branches e Commits**

- Verifica as suas branches como o comando

`git branch`

Aparecerão as branches e a branch atual, que será destacada em verde.

- Vamos agora criar uma nova branch em que trabalharemos num arquivo de
  texto mais simples para aprendermos a usar essas funcionalidades do
  git. Chamaremos essa branch de `textos`.

`git branch textos`

Verifique se ela foi criado com o comando

`git branch`

- Mude agora para a branch em que deseja trabalhar. Digite os seguintes
  comando:

`git checkout textos`

`git branch`

- Vamos agora fazer umas alterações pequenas no arquvio de texto, salvar
  e fechar o arquivo. Digite o seguinte comando abaixo para identificar
  qualquer modificação nos arquivos:

`git status`

- Adicione a modificação. Mas lembre que a modificaçõa ainda não foi
  para a branch master

`git add .`

`git status`

- Vamos fazer o commit dessa alteração (versionamento)

`git commit -m "Adicionando o sobrenome"`

- Estando tudo certo até agora, vamos fazer o `git push` para enviar ao
  Github

`git push`

Ele dá uma mensagem de erro quando criamos uma branch nova. Copie a
sugestão de comando e execute novamente.

`git push --set-upstream origin textos`

- Verifique agora no Github as duas versões do arquivo de texto em cada
  uma das branches, `textos` e `master`.

- Vamos, então realizar a MESCLAGEM da `textos` para a `master`. Vamos
  voltar ao terminal do Rstudio e digitar

`git branch`

Agora vamos unir o código. Você vai entrar na branch que vai receber as
atualizações, no caso a branch master com os seguintes comandos:

`git checkout master`

`git branch`

`git pull`

Agora podemos mesclar da `textos` para a `master`.

Recomenda-se antes de fazer a mesclagem, puxar as atualizaçãoes que
estão no servidor para a sua máquina , pois pode ser que algum outro
colega fez atualizações e você pode correr o risco de estar fazendo
mesclagem com uma versão antiga. Digite primeiro `git pull` e depois o
comando abaixo:

`git merge textos`

- Faça agora o git push (aqui você pode fazer assim e não pr_push)

`git push`

Agora vá na branch master do Github e verifique se o código foi
atualizado na master.

Só adicione os códigos que foram testados e estão funcionando
corretamente.

## **Mais um exercício**

Vamos criar mais uma linha no arquivo de texto (ou outra funcionalidade
qualquer

1.  Faça a atualização: `git pull` na master

2.  Crie a sua branch e mude para ela:
    `git checkout -b sistema-de-login master`

3.  Crie um novo arquivo txt chamado `sistema de login.txt` e salve-o.

4.  Digite `git add . && git status` e o arquivo ficará pronto para ser
    adicionado

5.  Confirme essas alterações: `git commit -m "Criado sistema de Login"`

6.  Digamos que tudo esteja funcionando e checado o código, volte para a
    master:

    `git checkout master && git branch`

7.  Atualize o código da master: `git pull`

8.  Agora sim, você pode mesclar: `git merge sistema-de-login master`

9.  Mande essa alteração para o servidor: `git push`

10. Observe no servidor do github as alterações

# **Criando um Pull Request**

Em alguns casos, só vamos conseguir unir códigos se fizermos uma
requisição para uma pessoa responsável pelo repositório através do
processo chamado Pull request. Vamos imaginar que você queira fazer
alterações via a branch sistema-de-login.

1.  Vamos entrar na nossa master `(git checkout master)`, fazer
    `git pull` e depois mudar para a branch sistema-de-login:
    `git checkout sistema-de-login`

2.  Altere o arquivo `sistema de login.txt` acrescenta a linha: “Digite
    sua idade**“** e salve o arquivo.

3.  Adicione : `git add . && git status`

4.  Agora faça commit:
    `git commit -m "Adicionado idade ao sistema de login"`

5.  Agora, seu código precisa ser mesclado por outro pessoa da equipe.
    Você faz um push e não mescla nada como feito acima. Digite de
    dentro da branch modificada: `git push`

6.  O Sitema vai pedir que digite um novo comando:
    `git push --set-upstream origin sistema-de-login`

7.  Veja página no Github e observará que aparece a branch
    sistema-de-login atualizada recentemente e que pede para comparar e
    fazer Pull Request. Clique em `Compare & Pull Request`

8.  O sistema muda para a janela indicando que a solicitação de
    mesclagem vai da branch sistema-de-login para a master

9.  Você pode explicar mais em comentários e clique em
    `Create Pull Request`

10. A pessoa que tiver o poder para fazer a revisão e mesclar, pode
    clicar em `Merge Pull Request`

# **Apagando a última modificação**

Caso aconteça algum erro, é possível voltar a momento anterior às
modificações (ou até ainda um prévio a este se os conflitos forem
grandes, mas **tenha muito cuidado em resetar commits mais antigos**).
Observamos que esta parte de rever mudanças pode não ser tão necessária,
pois usamos poucos linhass de códigos. Mesmo assim, vamos ver algumas
funções básicas , caso precise. Primeiro vemos o histórico de
atualizações.

1.  Digite `git reflog` no terminal e veja qual o identificador do
    commit (hash do commit, um número alfanumérico com 8 caracteres)
    anterior a essa modificação

2.  Para resetar a mudança, digite o comando seguinte acompanhado do
    identificador anterior : `git reset --hard 7d0932f`

3.  Caso vc se arrependa dessa eliminação, você pode voltar atrás,
    fazendo um `git reflog` e digitar o numero de identificação da
    modificação que se arrependeu de apagar: `git reset --hard 5a6cc0a`

4.  Veja a partir do minuto 23:00 do vídeo Curso de Git e Github
    Completo 2023 para mais esclarecimentos.

## **Considerações Finais**

- **Reverter um commit:** Mantém o histórico do commit original e
  adiciona um novo commit que desfaz as mudanças.

- **Resetar para um estado anterior:** Reescreve a história do
  repositório, removendo commits subsequentes.

- **Recomenda-se toda vez que fizer um commit, deve fazer `git push` ou
  `pr_push()`** antes de fazer novas alterações, para evitar a mensagem
  de 1 ou 2 commit a frente das modificações. Dá pra fazer, mas cuidado
  em fazer pull entre seu commit e seu push, pois pode gerar conflito de
  versões. Tudo para evitar trabalhar em versões não atualizadas.

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
