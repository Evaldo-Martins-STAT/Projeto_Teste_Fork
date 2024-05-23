
<!-- README.md é gerado a partir deste README.Rmd. Por favor, edite  e renderize este arquivo -->

# Modelo Para Controle de Version de Projetos (Clonar e/ou Bifurcar (Fork))

<!-- badges: start -->
<!-- badges: end -->

O Objetivo deste projeto chamdo **Projeto_Teste_Fork** é fornecer
informações necessários para usuários inciais e intermediários
aprenderem a usar o Git/Github na interface RStudio para Controle de
Versão de Projetos. A primeira parte usa as funções do pacote `usethis,`
e a partir da seção *Trabalhando com Versionamento*, usamos os comandos
do Git.

# Instruções Inicias para uso do Git/Github

1.  Crie uma conta gratuita no GitHub <https://github.com/>

2.  Descarregue o arquivo executável do Git neste link
    <https://git-scm.com/downloads>

3.  Instale o Git e depois abra e feche o Git Bash ao fim da instalação.
    Feche e reinicie o Rstudio para reconhecer o local de instalação do
    Git (NOrmalmente, *C:/Program Files/Git/bin/git.exe*).

4.  Instale o pacote `usethis` e carregue-o para configurar o Git para
    uso no Rstudio

``` r
library(usethis)
```

# Configure o Git/Github no RStudio

5.  Vamos usar o pacote `usethis` e os comando abaixo para parear com a
    sua conta remota no Github. Acesse o nome da sua conta e e-mail em
    Configurações –\> Perfil Público (Settings).

``` r
usethis::use_git_config(user.name = "Evaldo Martins", 
                        user.email = "evaldomartins@ufpa.br")
```

6.  Criar um novo token ou regenerar o token (codigo de 40 dígitos serão
    produzido)

``` r
usethis::create_github_token() # Muda para o site do Github para fazer login
```

Depois de fazer login, gere o token na própria página do Github e o
copie. Após copiar, Você deverá colocar esse número no arquivo
`.Renviron`. O `.Renviron` é um arquivo de configuração do R que permite
que você especifique variáveis de ambiente para que fiquem disponíveis
para o R. Ele é muito usado para disponibilizar senhas, chaves de API,
etc. - coisas que são secretas - e por isso não é boa prática colocá-las
no código. Então execute o seguinte comando:

7.  **Abra o arquivo .Renviron**

``` r
usethis::edit_r_environ()
```

8.  Crie uma nova linha nesse arquivo digitando primeiramente :
    GITHUB_PAT=SEU_TOKEN. Exemplo:

`GITHUB_PAT=ghp_Ko3mdlNJpBzQ7lvzKTvGFg91f6HpBQlablalba`

9)  Após adicionar o token copiado do site, pule uma linha e salve o
    arquivo.
10) Reinicie o RStudio: CTRL + SHIFT + F10

# Como criar repositório

## Criando repositório primeiro no Github

1.  A forma mais eficiente de criar repositório é fazer via o site do
    Github, pois tudo fica devidamente configurado

2.  Clique no notão verde **New**

3.  Preencha as informações conforme figura abaixo

<img src="images/clipboard-142360520.png" width="637" />

4.  Clone o repositório para que seja criado na sua máquina local

    Clique no botão verde **Code**. Copie a url do projeto para poder
    clonar.

<img src="images/clipboard-3984491672.png" width="376" />

**Baixe o repositório(Projeto) a partir do Github remoto:**

5.  Em seguida, no RStudio, você pode criar uma cópia desse repositório
    para trabalhar em **Projeto com Versionamento** indo em
    `File–> New projec`t e escolha a opção de `Version Control –> Git` e
    coloque a **url** do repositório e especifique a pasta onde este
    será salvo.

6.  Ao fazer desta maneira, seu respositório já fica vinculado ao git do
    seu computador e, obviamente, está pareado com o Github na internet.

    **Implemente pequenas mudanças no seu projeto para testes:**

7.  Faça pequenos testes de alteração no seu repositório testes, como:
    *criar pasta e arquivo nesta pasta, comitar (versionar) por meio da
    aba git botão `Commit`, realizar `Push`*`.`

8.  Verifique no servidor do Github as suas alterações.

9.  Agora, faça alteração no arquivo Readme no Github web, commit e
    depois faça Pull no RStudio. Observe no arquivo se houve a mudança.

## Inclua pastas e arquivos no arquivo .gitignore

Geralmente precisamos que arquivos e pastas não sejam
compartilhados/divulgados. Para isso, insira as pastas e arquivos no
arquivo .`gitignore`. Verifique neste Projeto_Teste_Fork quais pastas e
arquivos não são compartilhados.

## Criando o Repositório no Computador Primeiro

Não é a forma mais recomendada, mas é possível criar um repositório
pareado com o Github, no computador primeiro, da sequinte maneira:

``` r
usethis::create_project(path = "D:/Git/Clube_Codigo/Nome_Projeto")
usethis::use_git()    # Digite no console desse projeto para ligá-lo ao Git
usethis::use_github() # Digite no console desse projeto para levá-lo ao Github
```

**A partir de um projeto existente no computador:**

Você também pode criar a partir de um
`Projeto já existem em seu computador`. Primeiro carregue o projeto e
depois use as duas útlimas linhas de comando acima para ligá-lo ao Git e
carregá-lo ao Github.

## Clonando e bifurcando um respositório (fork)

Quando queremos trabalhar em colaboração com mais pessoas, podemos não
só clonar um respositório, mas também bifurcá-lo ao mesmo tempo. Para
isso, utilize os comandos abaixo.

``` r
usethis::create_from_github(
  repo_spec = "https://github.com/Evaldo-Martins-STAT/Projeto_Teste_Fork",
  destdir = "D:/Git/Clube_Codigo/",
  fork = TRUE)
```

# Contribuindo com um Projeto de Análise

Após ter criado uma cópia do repositório a partir do Github remoto
usando a opção de fork (Bifurcamento), você pode querer melhorar ainda
mais o código desse projeto de análise. Siga os passo abaixo para
inserir as suas linhas de código, seja em arquivos `*.R`, `*.Rmd`,
`*.qmd`, `*.csv`, `*xlsx`, ou quaisquer outros arquivos editáveis, ou
inserir outros não editáveis dentro das pasta do projeto.

1.  **Primeiro, sempre** crie um galho ou ramificação (**branch**) - A
    criação de branch é recomendada antes de alterar qualquer arquivo do
    projeto em que você pretende contribuir. É importante que você
    esteja na branch principal (master) e use o comando abaixo no
    console, dando nome apropriado à branch que reflita as modificações
    que deseja implementar.

``` r
usethis::pr_init(branch = "ajuda_grafico1")
```

2.  Agora, você pode começar a fazer as contribuições nos arquivos
    desejados ou mesmo criar novos arquivos e pastas. Faça uma pequena
    modificação no arquivo Readme.Rmd (Tabela abaixo, incluindo seu nome
    e e-mail). Depois renderize (aperte no botão `Knit`).

3.  Após término das suas alterações, realize o `Commit` (Botão na aba
    git)

4.  NÃO pressione o botão
    <span style="color: lightgreen;">**Push**</span> agora. A operação
    de “empurrar” deve feita via digitação da função
    **`usethis::pr_push()`** no console, seguida de `Enter`, a fim de
    criar uma Pull Request (PR).

    ``` r
    usethis::pr_push()
    ```

5.  A página do Github se abrirá para que você possa completae o
    `Pull Request (PR)`

6.  Então comente as mudanças que fez e clique em
    `Criar Requerimento Pull` (ou `Create Pull Request`)

7.  Aguarde o mantenedor do projeto fazer a mesclagem (Merge). Após a
    mesclagem, aparecerá o botão Merged (Ou Mesclado). Só então você
    finaliza sua contribuição, fechando a brunch no Rstudio

    **Obs1:** Quanto ao mantenedor, a mesclagem da branch de
    modificações com a branch master do projeto pode ser feita no
    Github. Após mesclar com a branch `master`, o mantenedor pode
    inclusive fazer pequenas alterações nas linhas de código recém
    mescladas e incluir um novo `Commit` e `Push`.

8.  Por sua vez, quando receber um aviso do mantenedor de que foi aceita
    a sua contribuição, o (a) colaborador (a) deve voltar para a branch
    `master` no RStudio, e então **clique primeiro** no botão
    <span style="color: lightblue;">**Pull**</span> da aba git para
    atualizar as contribuições suas mescladas e outras que eventualmente
    o mantenedor do repositório acrescentou.

9.  Volte à branch que você criou e delete-a usando a aba `Git` e
    digitando no console **usethis::pr_finish().**

    ``` r
    usethis::pr_finish()
    ```

10. Pronto, você está com a versão mais atualizada na sua brach
    principal (master)

    **Obs2**: Como boa prática, sempre comunique o mantenedor de suas
    modificaçãoes.

**Cadastre seu nome e endereço de e-mail abaixo:**

| \#  |              Nome              |          e-mail           |
|:---:|:------------------------------:|:-------------------------:|
|  1  |    Evaldo Martins da Silva     |   evaldomartins@ufpa.br   |
|  2  | Rayane Leticia Furtado Pinheio | rayanefurtado63@gmail.com |
|  3  |                                |                           |
|  4  |                                |                           |
|  5  |                                |                           |
|  6  |                                |                           |
|  7  |                                |                           |

Lista de Colaboradores do Projeto (Repositório).

# **Trabalhando com versionamento no Terminal**

De agora em diante, vamos trabalhar via Terminal do RStudio a fim de
trabalhar de forma mais profissional com versionamento.

## **Verificando o histórico de atualizações**

Certifique-se de que você está no diretório do projeto, digitando
`getwd()` no console. Agora vamos ver o histórico de comando. Digite no
terminal:

`git reflog`

A aparecerá uma lista de todos os commits (versionamentos) que você já
fez no projeto e de seus colaboradores. Vamos agora exercitar o que já
fizemos com as funções do pacote usethis, desta feita com os comandos do
Git.

## **Criação de Branches e Commits**

- Verifica as suas branches locais como o comando

`git branch`

Aparecerão as branches e a branch atual, que será destacada em verde.

- Vamos agora criar uma nova branch em que trabalharemos num arquivo de
  texto mais simples para aprendermos a usar essas funcionalidades do
  git. Chamaremos essa branch de `textos`.

`git branch textos`

Verifique se ela foi criado com o comando ou na aba Git d Rstudio

`git branch`

- Mude agora para a branch em que deseja trabalhar. Digite os seguintes
  comando:

`git checkout textos`

`git branch`

- Vamos agora fazer umas alterações pequenas no arquivo de texto, salvar
  e fechar o arquivo. Digite o seguinte comando abaixo para identificar
  qualquer modificação nos arquivos:

`git status`

- Adicione a modificação. Mas lembre que a modificaçõa ainda não foi
  para a branch master

`git add .`

`git status`

- Vamos fazer o commit dessa alteração (versionamento)

`git commit -m "Adicionando o sobrenome"`

- Estando tudo certo até agora, faça o `git push` para enviar ao Github

`git push`

Ele dá uma mensagem de erro quando criamos uma branch nova. Copie a
sugestão de comando e execute novamente.

`git push --set-upstream origin textos`

- Verifique agora no Github as duas versões do arquivo de texto em cada
  uma das branches, ou seja, `textos` e `master`.

- É preciso, então, realizar a MESCLAGEM da `textos` para a `master`. Se
  vc for o mantendedor do projeto, volte ao terminal do Rstudio e
  digite:

`git branch`

Agora vamos unir o código. Você vai entrar na branch que vai receber as
atualizações, no caso a branch master com os seguintes comandos:

`git checkout master`

`git branch`

Agora podemos mesclar da `textos` para a `master`.

**Obs**: Recomenda-se antes de fazer a mesclagem, puxar as atualizaçãoes
que estão no servidor para a sua máquina, pois pode ser que algum outro
colega fez atualizações e você pode correr o risco de estar fazendo
mesclagem com uma versão antiga. Digite os comandos abaixo:

`git pull`

`git merge textos`

- Faça agora o git push para enviar ao Github remoto

`git push`

Agora vá na branch master do Github remoto e verifique se o código foi
atualizado na master. Só adicione os códigos que foram testados e estão
funcionando corretamente.

- Finalmente, `apague a branch localmente.` Mude para outra branch, como
  a master e apague a branch local

  `git checkout master`

  `git branch -d nome-da-branch`

- Se quiser forçar a exclusão de uma branch se ela ainda não foi
  mesclada, use:

  - `git branch -D nome-da-branch`

- Para apagar a branch no repositório remoto, você precisa usar o
  seguinte comando

  `git push origin --delete nome-da-branch`

**Obs: Caso não seja o mantenedor do projeto,** veja como se faz o
processo de alterar/comitar/empurrar/mesclar/apagar branch em *Criando
uma Pull Request* usando o terminal.

## **Mais um exercício**

Vamos criar mais uma linha no arquivo de texto (ou outra funcionalidade
qualquer no projeto)

1.  Faça a atualização: `git pull` na master

2.  Crie a sua branch e mude para ela:
    `git checkout -b sistema-de-login master`

3.  Crie um novo arquivo txt chamado `sistema de login.txt` e salve-o.

4.  Digite `git add . && git status` e o arquivo ficará pronto para ser
    adicionado

5.  Confirme essas alterações: `git commit -m "Criado sistema de Login"`

6.  Digamos que tudo esteja funcionando e checado o código remotamente,
    volte para a master:

    `git checkout master && git branch`

7.  Atualize o código da master: `git pull`

8.  Agora sim, você pode mesclar: `git merge sistema-de-login master`

9.  Mande essa alteração para o servidor: `git push`

10. Observe no servidor do github as alterações

11. Apague a branch:
    `git checkout master && git branch -d nome-da-branch`

# **Criando um Pull Request**

Em alguns casos, só vamos conseguir unir códigos se fizermos uma
requisição para uma pessoa responsável pelo repositório através do
processo chamado Pull request. Vamos imaginar que você queira fazer
alterações via a branch sistema-de-login.

1.  Vamos entrar na nossa master `(git checkout master)`, fazer
    `git pull` e depois mudar para a branch sistema-de-login:
    `git checkout sistema-de-login`

2.  Altere o arquivo `sistema de login.txt` acrescentando a linha:
    “Digite sua idade**“** e salve o arquivo.

3.  Adicione : `git add . && git status`

4.  Agora faça commit:
    `git commit -m "Adicionado idade ao sistema de login"`

5.  Agora, seu código precisa ser mesclado por outra pessoa da equipe.
    Você faz um push e não mescla nada como feito acima. Digite de
    dentro da branch modificada: `git push`

6.  O Sitema vai pedir que digite um novo comando:
    `git push --set-upstream origin sistema-de-login`

7.  Veja página no Github e observará que aparece a branch
    sistema-de-login atualizada recentemente e que pede para comparar e
    fazer Pull Request. Clique em `Compare & Pull Request`

8.  O sistema muda para a janela indicando que a solicitação de
    mesclagem vai da branch sistema-de-login para a master

9.  Você pode explicar mais em comentários ao mantenedor sibre sua
    contribuição e clique em `Create Pull Request`

10. A pessoa que tiver o poder para fazer a revisão e mesclar, pode
    clicar em `Merge Pull Request`

# **Apagando a última modificação**

Caso aconteça algum erro, é possível voltar ao momento anterior às
modificações (ou até ainda a um anterior a este se os conflitos forem
grandes, mas **tenha muito cuidado em resetar commits mais antigos**).
Observamos que esta parte de reverter mudanças pode não ser tão
necessária, pois usamos poucos linhass de códigos. Mesmo assim, vamos
ver algumas funções básicas , caso precise. Primeiro vemos o histórico
de atualizações.

1.  Digite `git reflog` no terminal e veja qual o identificador do
    commit (`hash do commit`, um número alfanumérico com 8 caracteres)
    anterior a essa modificação

2.  Para resetar mudanças posteriores, digite o comando seguinte
    acompanhado do identificador anterior : `git reset --hard 7d0932f`

    **Obs:** Caso vc se arrependa dessa eliminação, você pode voltar
    atrás, fazendo um `git reflog` e digitar o numero de identificação
    da modificação que se arrependeu de apagar:
    `git reset --hard 5a6cc0a`

3.  Mas se vc quer continuar com a modificação, você precisará que o
    histórico local do seu repositório não fique atrás do histórico
    remoto. Você deve forçar que o histórico remoto seja igual ao local
    (o que pode sobrescrever alterações remotas, para isso tenha certeza
    da modificação). Você deve usar o comando  
      
    **`git push --force`**

    Obs: veja a partir do minuto 23:00 do vídeo
    `Curso de Git e Github Completo 2023` para mais esclarecimentos.

## **Considerações Finais**

- **Reverter um commit:** Mantém o histórico do commit original e
  adiciona um novo commit que desfaz as mudanças.

- **Resetar para um estado anterior:** Reescreve a história do
  repositório, removendo commits subsequentes.

- **Recomenda-se toda vez que fizer um commit, fazer `git push` ou
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

Res.: Você pode incluir chunks como este:

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
