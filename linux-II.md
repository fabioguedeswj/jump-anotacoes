# Comandos Linux

## Comandos de processos

| Comando | Descrição |
| --- | --- |
| ps | mostra os processos  do terminal |
| ps -e | mostra todos os processos |
| ps -ef | processos + informações |
| ps -e &#124; grep (processo) | o grep é um programa que filtra |
| pstree | árvore de processos |
| kill (num processo) | mata o processo |
| kill -9 (num processo) | mata o processo de vez |
| killall (nome) | mata tudo com X nome |
| sudo service (processo) stop | paro o serviço | 
| sudo service (processo) start| inicio o serviço | 
| top | mostra consumo de CPU / memória |

## Comandos de execução

| Comando | Descrição |
| --- | --- |
| (programa) | abre o programa |
| ctrl + z | pausa o processo |
| jobs | lista os processos pausados ou executando em segundo plano|
| bg (num programa) | executa o programa em background |
| fg (num prorgama | traz o programa pro foreground) |
| (programa) & | executa o programa direto no background |
| sh (programa) | executa um script criado (precisa de permissão de execução) |


## Comandos de permissão

- Grupos: user (u) | group(g) | others(o)
- Cada grupo pode ter as seguintes permissões: read (r), write (w), execute (x)

| Comando | Descrição |
| --- | --- |
| ls -l | mostra as permissões dos arquivos no diretório |
| chmod (u,g,o,a)(+,-r,w,x) (arquivo) | muda permissões |

Exemplo: chmod ug+x arquivo.txt (adiciono para o user o o group a permissão de execução no arquivo.txt) 


## Comandos de localização

| Comando | Descrição |
| --- | --- |
| locate (arquivo) | encontra um arquivo |
| which (programa) | procura o caminho do arquivo que será executado |
| sudo updatedb | atualiza o banco de dados do sistema |

Obs.: o 'sudo' executa como se fosse o usuário root

## Comandos de usuário

| Comando | Descrição |
| --- | --- |
| adduser (nome) | adiciona um novo usuario (apenas root) |
| passwd | muda senha do usuario |
| sudo passwd | muda senha do root |
| su (usuario) | muda de usuario |


## Comandos de instalação

| Comando | Descrição |
| --- | --- |
| sudo apt-get update | atualiza a lista de programas |
| apt-cache search (vsftp) | busca por um programa |
| sudo apt-get install (vsftpd) | instala o programa |
| sudo apt-get remove (vsftpd) | remove o programa |

Obs.: o 'vsftpd' é um exemplo

### Outra maneira de instalar

Buscar por "vsftpd .deb" no google ao invés de usar o apt-get. Com o arquivo "em mãos", fazer o seguinte:

| Comando | Descrição |
| --- | --- |
| sudo dpkg -i (nome do download) | instala |
| sudo dpkg -r (nome do pacote) | desinstala |

## Conexão remota com SSH

| Comando | Descrição |
| --- | --- |
| sudo apt-get install ssh | instala o SSH |
| ssh nome@localhost | faço a conexão remota |
| ssh -X nome@localhost | conexão com gráfico |
| scp (arquivo) nome@localhost:~/ | copia o arquivo para o diretorio remotamente|
