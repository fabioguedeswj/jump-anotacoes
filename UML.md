# UML

UML se baseia na orientação a objetos para representar diagramas. Cada diagrama é composto por elementos (formas gráficas) que possuem relação entre si.

## Diagrama de caso de uso

Esse diagrama deixa claro o que tem no sistema e quais usuários vão interagir com essas funcionalidades

Exemplos:
- Comprar um curso **(funcionalidade)** -> Aluno **(ator)**

- Assistir ao video, responder aos exercicios **(funcionalidade)** -> aluno **(ator)**

- Revisar exercicios **(funcionalidade)** -> professor **(ator)**

Obs.: a seta vai do ator pra funcionalidade

Se eu puxar uma seta de uma funcionalidade pra outra eu crio uma realção de dependencia (puxa a seta do assistir video para o comprar curso, porque assistir o vídeo depende que o aluno compre um curso)

### Alguns esteriótipos

- &#60;&#60;depends&#62;&#62; gera uma relação de dependencia
- &#60;&#60;extends&#62;&#62; extende algo. Exemplo: "Boleto" &#60;&#60;extends&#62;&#62; comprar curso


## Diagrama de classes

Uma classe é representada por um quadrado cuja:

- Primeira informação é o nome da classe
- Informação central são os atributos
- Por último vem os métodos

Obs.: o - indica que é privada e o + que é publica (normaalmente atributos são privados e métodos são públicos)

| Nome da classe |
| ---- |
| Atributos |
| Métodos |

### Algumas simbologias

- Uma seta com um diamante entre classes significa composição. Por exemplo. se o diamante estiver do lado de uma classe chamada alunos e a outra ponta da linha ligar a classe contrato, lê-se: aluno contêm contrato

- Uma seta de uma classe para outra indica que esta está herdando os atributos

- Apenas a linha indica alguma relação 


## Diagrama de sequência

É mais usado quando existe um "vai e vem" nos processos.


## Diagrama de atividades

### Algumas simbologias

- Circulo: inicio da atividade

- Retangulo: mostra os passos

- Duas setas saindo de um retangulo: escolha

- Um retanguluzinho (width: 20px height: 80px) com duas ou mais setas saindo dele: a atividade acontece simultaneamente

- Um diamante: representa uma condicional

- Uma bola pintada: acabou a atividade (não é totalmente pintada, é tipo um circulo concentrico)



## Diagrama de estados

O estado fica dentro de um círculo. 

Exemplo: estados de um contrato:

- Temporário
- Válido
- Cancelado

(pode ter mais)

O desenho do inicio é um circulo

"Estou em um contrato temporário, se o pagamento falha eu vou pro cancelado, se é aprovado vou pro Válido" - ligo isso com setas


## Diagrama de componentes

Mostra como os sistemas conversam entre si

- Site de vendas (sistema) - o desenho é um retangulo com dois quadrados desenhados na lateral

- Paypal (outro sistema &#60;&#60;externo&#62;&#62;)

- O site de vendas conversa com paypal via http (liga uma seta e escreve http)
