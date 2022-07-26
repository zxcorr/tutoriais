1) Para instalar um programa localmente (sem sudo)::

	wget <file_url>

Caso esteja compactado::

	tar xvf <file_name>
	
2) A partir daqui é recomendado seguir o README::

	more README.rst
	
---------------------------------------------------
	
De modo geral os passos seguintes costumam ser como consta abaixo.

3) Criar diretório onde deverão ficar os arquivos::

	mkdir <novo_diretorio>
	
3) Executar o arquivo de configuração::

	./configure --prefix=<caminho_do_novo_diretorio>
	
Caso não exista um arquivo configure, pode-se tentar::

	make configure
	
e em seguida fazer executar configure acima.
	
4) Executar o make::

	make
	
Ou, alternativamente (rodar com 8 núcleos)::

	make -j 8
	
5) E por fim, executar o make install::

	make install
	
Aqui termina a instalação. 

6) Para poder executar o programa, é necessário atualizar o PATH do sistema:

	export PATH=${PATH}:<caminho_do_novo_diretorio/bin>
	
Caso deseje alterar o PATH permanentemente, deve alterar no arquivo ~/.bash_profile da seguinte forma::

	export PATH="<caminho_do_novo_diretorio/bin>:$PATH"
	
As alterações irão funcionar na próxima sessão. Caso deseje aplicá-las imediatamente, basta atualizar o shell atual com o comando source::

	source ~/.bash_profile
