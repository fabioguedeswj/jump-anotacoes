# Git e Github

**Git** é um sistema de controle de versões que permite o armazenamento e acesso ao histórico de modificações em um servidor específico, possibilitando um melhor trabalho em equipe

**Github** permite criar repositórios git

## Comandos git

### Comandos de inicialização

| Comando | Descrição |
| ---- | ---- |
| git init | inicializa o repositorio do git dentro da pasta |
| git init --bare | cria um local de armazenamento |

Obs.: o --bare que cria um repositório na minha máquina. Quando eu faço a conexão remota, eu passo o diretório desse arquivo, e não de um repositório no github

### Comandos básicos

| Comando | Descrição |
| ---- | ---- |
| git status | mostra o estado do repositório |
| git config --local user.name (nome) | informa 'quem é você' |
| git config --local user.email (email) | informa 'quem é você' |
| git add (arquivo) | adiciona o arquivo na "fila de espera" |
| git add . | adiciona todos os arquivos na "fila de espera |
| git commit -m "mensagem" | adiciona uma mensagem a versão |
| git log | permite ver o histórico de atualizações |
| git log --oneline | histórico em uma linha |
| git log -p | histórico completo |

### Comandos de repositório

| Comando | Descrição |
| ---- | ---- |
| git remote add (nome do repositorio) endereço| adiciona um repositório |
| git remote | lista os repositorios remotos |
| git clone (diretório) (nome da pasta que vai criar) | faz uma cópia do repositóio |
| git push (nome-repositorio) (branch) | empurra os arquivos pro repositório|
| git pull (repositorio) (main) | pega os dados do repositorio remoto |
| git remote rename (atual) (novo) | altera o nome do repositorio |

### Comandos de branch

| Comando | Descrição |
| ---- | ---- |
| git branch | mostra os branches |
| git branch (nome) | cria um novo branch |
| git checkout (nome) | muda de branch |
| git checkout -b (nome) | cria um branch e muda pra ele |
| git merge (em qual?) | faz um merge do branch atual com o informado e cria um commit pra esse merge|
| git rebase (em qual?) | faz um merge, mas joga os commits da branch informada na branch que fez o rebase |

### Comandos para desfazer alterações

| Comando | Descrição |
| ---- | ---- |
| git checkout -- (arquivo) | desfaz alterações antes do 'add' |
| git reset HEAD (arquivo) | "tira" o arquivo do 'add' |
| git revert (hash do commit) | desfaz o commit |
| git checkout (hash do commit) | deixo o código na versão do commit |

Obs.: se eu quiser fazer alterações que serão modificadas eu preciso criar um novo branch (falando sobre o checkout (hash))

### Comandos de save temporário

| Comando | Descrição |
| ---- | ---- |
| git stash | salva temporariamente pra terminar depois |
| git stash list | lista tudo que está salvo |
| git stash pop | traz a alteração de volta como um merge |

### Comandos para ver alterações

| Comando | Descrição |
| ---- | ---- |
| git diff | mostra o que foi alterado e não adicionado |
| git diff (hash1)..(hash2) | mostra a diferença entre dois commits |

### Comandos de TAG

| Comando | Descrição |
| ---- | ---- |
| git tag -a (nome) -m "mensagem" | adiciona um marco na aplicação |
| git tag | mostra as tags disponíveis |
| git push (repositório) (nome da tag) | envio a tag |


### Resolvendo conflitos no merge

<<<<<< HEAD

Mostra os dados que estão no commit atual

'==========

Mostra os dados que estou tentando trazer
  
'>>>>>>>

- Preciso escolher qual eu quero antes de pushar

- Depois que corrigir, basta dar um 'git commit -m 'mensagem'' pra atualizar e pushar
