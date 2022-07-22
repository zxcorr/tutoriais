Para instalar um programa localmente (sem sudo)::

	wget <file_url>

Caso esteja compactado::

	tar xvf <file_name>
	
A partir daqui é recomendado seguir o README::

	more README.rst
	
---------------------------------------------------
	
De modo geral os passos seguintes costumam ser como consta abaixo.

Criar diretório onde deverão ficar os arquivos::

	mkdir <novo_diretorio>
	
Executar o arquivo de configuração::

	./configure --prefix=<caminho_do_novo_diretorio>
	
Executar o make::

	make
	
Ou, alternativamente (rodar com 8 núcleos)::

	make -j 8
	
E por fim, executar o make install::

	make install
	
Aqui termina a instalação. Para poder executar o programa, é necessário atualizar o PATH do sistema:

	export PATH=${PATH}:<caminho_do_novo_diretorio/bin>
	
