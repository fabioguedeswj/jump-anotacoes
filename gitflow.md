# Gitflow

O gitflow é um fluxo de trabalho que dita regras entre branches, merges, nomenclatura. É importante dizer que ele não adiciona novos comandos, apenas atribui funções específicas para as diferentes ramificaçõese e quando elas devem interagir.

## Ramificaçõse

- main: armazena o histórico de lançamento oficial
- develop: serve como integração para recursos
- feature: adiciona novos recursos
- release: prepara o lançamento de uma nova versão
- Hotfix: servem para manutenção

### Feature

- Cada nova feature deve residir na própria ramificação

- As ramificações feature usam a ramificação develop como pai. Quando uma feature é concluida, ela passa por merge de volta para ramificação de desenvolvimento (develop)

- As features nunca devem interagir direto com a ramificação main

### Release

- Quando a ramificação develop adquire features suficientes para um lançamento, você bifurca uma ramificação release a partir da ramificação develop 

- Nenhuma nova feature pode ser adicionada depois desse ponto, apenas atualizações de segurança, geração de documentação e outras tarefas relacionadas ao lançamento

- Quando estiver pronto para ser lançada, a ramificação release passa por merge para ramificação main e é marcada com o número da versão

- Ela também deve passar por um merge de volta para ramificação develop, que pode ter progredido desde que o release foi iniciado

- O uso da ramificação dedicada ao preparo de release possibilita que uma equipe aperfeiçoe o lançamento atual enquanto outra equipe continua a trabalhar nos recursos para a próxima release

- As ramificações de release também são baseadas na ramificação de develop

- Depois do merge com o main e o develop, a ramificação release é excluida

### Hotfix

- são ramificações de manutenção usadas para corrigir com rapidez lançamentos de produção

- Ela é a **única** que deve ser bifurcada da ramificação main, assim que for concluida, deve ser feito o merge tanto na main quanto na develop (a ramificação main deve ser marcada com o número da versão atualizado)

- Ter uma linha de desenvolvimento dedicada para atualizações de segurança permite que sua equipe aborde problemas sem ter que interromper o resto do fluxo de trabalho ou esperar o próximo ciclo de lançamento.


