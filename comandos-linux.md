# Comandos Linux

## Comandos Básicos

| Comando | Descrição |
| --- | --- |
| pwd | mostra o caminho do diretório em questão |
| ls | lista o conteúdo do diretório |
| echo "aqui seu texto | o terminal reproduz a texto |
| echo "aqui seu texto" > (arquivo).txt | cria um arquivo com o texto |
| echo "aqui seu texto" >> (arquivo).txt | adiciona o texto ao arquivo |
| cat (arquivo).txt | lê o conteúdo do arquivo |
| man (comando) | mostra o manual do comando |
| (comando) --help | mostra o manual do comando |
| whoami | mostra o nome do usuário |
| clear | limpa o terminal |

## Modificadores

| Comando | Descrição |
| --- | --- |
| -l | listar longo (long) |
| -a | mostra tudo, até os ocultos (all) |
| -q | oculta detalhes (quiet) |
| -v | mostra mais detalhes (verbose) |

## Comandos de Navegação

| Comando | Descrição |
| --- | --- |
| cd (diretório) | vai para o diretório |
| cd | vai para o diretório base |
| . | diretório atual |
| .. | diretório anterior |
| / | diretório raiz |
| /home | diretório de cada um dos usuários |

## Comandos de Manipulação

| Comando | Descrição |
| --- | --- |
| mkdir (diretório) | cria um diretório |
| rmdir (diretório)| remove diretórios (apenas vazios) |
| rm (arquivo) | remove um arquivo |
| rm -r (diretório) | apaga o diretório com tudo dentro |
| cp (arquivo).txt (arquivo).txt | copia de um lugar para o outro (no caso de diretórios precisa usar o -r) |
| mv (arquivo).txt (arquivo).txt | move (ou renomeia) de um lugar para o outro |
| touch (aquivo) | 'encosto' no arquivo pra alterar a data (se existir) |
| touch (aquivo) | cria um arquivo (se não existir) |

## Comandos de Compactação

| Comando | Descrição |
| --- | --- |
| zip (nome).zip (diretório) | cria um zip do diretorio |
| zip -r (nome).zip (diretório) | cria um zip do conteudo do diretorio |
| unzip nome.zip | descompacta |
| unzip -l nome.zip | mostra o que tem dentro do arquivo |
| unzip -q nome.zip | descompacta sem mostrar as informações |

| Comando | Descrição |
| --- | --- |
| tar -cz (diretório) > (nome).tar.gz | cria um arquivo compactado |
| tar -czf (nome).tar.gz (diretorio) | cria um arquivo compactado |
| tar -xz < (nome).tar.gz | extrai o arquivo |
| tar -xzf (nome).tar.gz | extrai o arquivo |

## Comandos de Manipulação de arquivos grandes

| Comando | Descrição |
| --- | --- |
| head (arquivo).txt | tipo o 'cat', mas retorna os primeiros parágrafos |
| head -n (num parágrafos) (aquivo).txt | especifico o número de parágrafos |
| tail (arquivo).txt | Retorna os últimos parágrafos |
| tail -n (num parágrafos) (aquivo).txt | especifico o número de parágrafos |
| less (arquivo).txt | abre o arquivo no terminal |

## Editor VI

| Comando | Descrição |
| --- | --- |
| vi (arquivo).txt | abre o arquivo no terminal com o editor VI |

### "Dentro" do editor VI

| Comando | Descrição |
| --- | --- |
| i | adiciona caracter antes |
| a | adiciona caracter depois |
| x | remove caracter |
| dd | remove a linha |

| Comando | Descrição |
| --- | --- |
| esc | vai pro modo de navegação |
| shift + g | vai pra última linha |
| número + shift + g | vai pra linha em questão | 
| $ | vai pro final da linha atual 
| 0 | vai pro primeiro caracter da linha |

| Comando | Descrição |
| --- | --- |
| /(palavra buscada) | localiza determinada palavra |
| n | próxima ocorrência da palavra procurada |
| shift + n | ocorrência anterior da palavra procurada |

| Comando | Descrição |
| --- | --- |
| yy | copia a linha |
| p | cola |
| (numero)yy | copia n linhas |
| (numero)p | cola n vezes |

| Comando | Descrição |
| --- | --- |
| :w | salva |
| :q | sair |

## Coringas

| Comando | Descrição |
| --- | --- |
| ? | um caracter |
| * | qualquer coisa |

