Introdução a Bash
=======================================================

Referências:
https://ryanstutorials.net/linuxtutorial/



Comandos Básicos
-------------------------------------------------------


1) Mudar de diretório::

	cd <destino>
	
	
2) Listar conteúdo de um diretório::

	ls <caminho>
	
Caso seja o diretório atual, apenas "ls" é suficiente.


3) Mostrar endereço do diretório atual (print working directory)::

	pwd


4) Mudar as permissões de acesso (leitura, escrita ou execução) de um arquivo::

	chmod <opções> <arquivo>
	
As opções têm a seguinte estrutura: <usuário><tipo><acesso>, em que:

* Usuário: indica aqueles que terão a permissão modificada. Pode ser "u" (dono do arquivo), "g" (grupo de usuários do arquivo), "o" (usuários não-membros do grupo) ou "a" (todos).
* Tipo: indica se a permissão será concedida ("+"), revogada ("-") ou redefinida ("=").
* Acesso: indica se a permissão será para modificar arquivos ("r"), ler arquivos ("r") ou executar arquivos ("x").

Exemplos:

Conceder permissão mais geral possível::

	chmod a+rwx <arquivo>

Revogar permissão de escrita de diversas pastas (flag de recursão -R) para o usuário::

	chmod u-w -R <arquivo>


5) Copiar um arquivo::

	cp <origem> <destino>
	
Caso deseje copiar uma pasta inteira, colocar a flag "-R" para que copie os arquivos recursivamente::

	cp -r <origem> <destino>
	
	
6) Mover um arquivo::

	mv <origem> <destino>

Esse comando também é usado para renomear arquivos. Basta movê-lo para o mesmo local com um nome diferente.


7) Remover (permanentemente!!!) um arquivo::

	rm <arquivo>
	
Utilizar a flag -r (recursivo) para remover diretórios inteiros.
**Atenção**: cuidado ao utilizar o comando. "rm -R /" remove a pasta root (arquivos do sistema).


8) Criar um arquivo em branco::

	touch <nome-do-arquivo>
	
	

Servidores
-------------------------------------------------------


1) Acessar um servidor (computador remoto)::

	ssh <nome-de-usuario>@<nome-do-servidor>
	
e inserir a senha em seguida.

Para visualização gráfica, acesse com a flag -X.


2) Copiar arquivos do servidor para máquina local ou vice-versa::

	scp <origem> <destino>
	
Usar a seguinte estrutura para o arquivo no servidor:: 

	<nome-de-usuario>@<nome-do-servidor>:<arquivo>



Outros Comandos
-------------------------------------------------------


1) Criar variáveis::

	<nome-da-variavel> = <conteudo-da-variavel>
	
Para acessar o conteúdo, utilizar o símbolo $::

	$<nome-da-variável>
	
Variáveis ficam apenas disponíveis no processo atual. Caso deseje que fique disponível em processos seguintes (outros bashes), ela deve ser exportada::

	export <nome-da-variavel>
	
Variáveis especiais: PATH, 0-9, #, @, ?, $, USER, HOSTNAME, SECONDS, RANDOM, LINENO.
	
	
2) Print::

	echo <conteudo>
	
Exemplo::

	var1 = "~/Documentos/"
	echo $var1
	

3) Criar uma sequência de números inteiros::

	seq <inicial> <final>
	
Ou:

	{<inicial>..<final>..<passo>}
	
O passo apenas está disponível em versões de Bash4.x em diante.


4) Fazer um laço::

	for <item> in <sequencia>; do <comandos>; done
	
Exemplos::

	for id in 0 1 2 8; do echo "id atual: $id"; done
	
	for number in $(seq 1 25); do echo "numero atual: $number"; done
	
	for hour in {0..23}; do echo "Hora: $hour"; done
	
	echo "Arquivos no diretorio atual:"
	for file in ./*; do echo "$file"
	
	for file  
