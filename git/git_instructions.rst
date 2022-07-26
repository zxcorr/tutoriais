#################################
Usando Git
#################################


=================================
 Introdução
=================================

Um **repositório** é uma estrutura de dados que guarda os metadados relativos a um conjunto de arquivos ou estrutura de diretórios, permitindo a verificação de alterações realizadas nos arquivos e o controle de versões, sendo bastante útil no desenvolvimento de softwares. 

O **git** é um sistema de gerenciamento de repositórios. É muito utilizado em projetos que necessitem de colaboração, ou então apenas para rastreamento das alterações nos arquivos locais de um usuário.

Existem serviços de manutenção de **repositórios remotos** (na nuvem), tais como Github e Bitbucket.
 
Todo repositório incia-se contendo apenas uma *branch* (ramo), chamada *main* (antiga master no github). Quando se deseja desenvolver diferentes aspectos de um projeto porém sem alterar diretamente a main, pode-se criar uma nova branch, que será uma cópia independente da main. Não há limite de branches para um repositório. Quando uma branch chega em um ponto satisfatório de desenvolvimento, e concorda-se que as modificações devem ser integradas à branch main, então realiza-se um *merge*, em que as alterações dessa branch serão incorporadas a outra branch.
  
Uma ótima sugestão de referência é o tutorial do Bitbucket:

https://www.atlassian.com/br/git/tutorials

=================================
 Local
=================================


-------------
Config
-------------

Inicializar seu usuário. Apenas uma vez por computador::

 git config --global user.name “Your Name Comes Here”
 git config --global user.email you@yourdomain.example.com


-------------
Init
-------------

Inicia repositório **local** na pasta::

 git init

Verifica o status do seu repositório local::

 git status

Remover .git (deleta o repositório local!)::

 rm -rf .git/


-------------
Branch
-------------
Cria uma branch::

 git branch <nome-da-branch>
 
A branch principal se chama "main". Antigamente era "master".

Alternar entre branches::

 git checkout <nome-da-branch>

Alterar o nome da branch deafault inicial::

 git config --global init.defaultBranch main


-------------
Staging
-------------
Marca arquivos a serem adicionados ao commit::

 git add <file1> <file2>

marcar tudo::

 git add . 

Removendo arquivos do stage::

 git restore --staged <file>


-------------
Commit
-------------
Realizar o **commit**::

 git commit -m "mensagem"

Desfazer um commit (antes de dar o push)::

 git reset --soft HEAD^
 git reset HEAD <file_to_remove>


-----------
Stash
-----------

Um stash guarda o estado atual do repositório sem fazer um commit, revertendo o repositório para o último commit feito. Seu propósito é salvar temporariamente mudanças realizadas mas que não estão prontas para um commit::

 git stash

Para aplicar as mudanças salvas no stash::

 git stash apply

Para limpar o que foi salvo no stash::

 git stash drop
 
O comando pop é a junção do apply e em seguida do drop::

 git stash pop

Também pode ser usado quando se realizou mudanças em uma branch indesejada. Nesse caso, realiza-se o stash, em seguida o checkout, e depois o apply e o drop.


=================================
 Remote
=================================


-------------
Remote
-------------

Conectar o repositório local a um repositório **remoto**::

 git remote add <remoto> <url>

Normalmente chamamos o principal de "origin" mas outros repositórios remotos podem ser adicionados a um mesmo repositório local.


-------------
Pull
-------------

**Atualizar** seu repositório local com a versão remota (baixa os arquivos remotos, sobrescrevendo os locais)::

 git pull <origin> <branch>

Para dar um push, é necessário que a sua versão esteja atualizada, exigindo então um pull caso não esteja.

Atualizar as *informações* do seu repositório local com a versão remota (é diferente do pull pois não sobrescreve os dados, apenas atualiza para o git se há novas branches, mudanças nas branches, etc., permitindo que você verifique e.g. git status)::

 git fetch <remoto>


-------------
Push
-------------

**Enviar** alterações locais para o repositório remoto::

 git push -u <remoto> <branch>


-------------
Clone
-------------

Clonar um repositório::

 git clone <url>
 
Clonar branch específica::

 git clone --branch <branch-name> <url>

Clonar branch específica sem trazer tooodo o histórico::

git clone --single-branch --branch <branch-name> <url>

