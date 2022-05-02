# Magento

## Escopo

A instalação do Magento possui a seguinte hierarquia: website, store e store view. Se formos considerar escopos, também temos o escopo global, que é aplicado para toda hierarquia do Magento. (Por exemplo, o código postal possui escopo global visto que é um valor aplicado para todo sistema)

<p align="center" width="250">
  <img src="https://user-images.githubusercontent.com/102316177/165958318-008d4ad5-8435-40d9-b54e-128deef9697d.png" width="650">
</p>

### Definição dos escopos:

**Global:** configurações disponíveis para todo sistema

**Website:** tem seu próprio domínio. As configurações são limitadas ao Website atual e cada um possui uma Store padrão

**Store:** as configurações são limitadas ao Store atual. Compartilham o mesmo catálogo mas podem exibir variações de produtos diferentes

**Store view:** as configurações são limitadas ao Store view atual. É comum usar store views para oferecer idiomas diferentes em uma mesma Store

## Estrutura do Magento

### Temas

**pasta do projeto > app > design > frontend:** aqui é criada a pasta com o vendor (fornecedor) e, dentro dessa pasta, outra pasta com o nome do tema. Essa pasta possui dois arquivos obrigatórios, sendo eles: 'registration.php' e 'theme.xml'.

<p align="center" width="250">
  <img src="https://miro.medium.com/max/346/1*Oif7iS53XZ2Eb3Nbxs5Ceg.png">
</p>

- O arquivo 'registration.php' serve para registrar o tema através da variável "register". Essa variável recebe 3 parâmetros:
  - A constante 'THEME' para indicar que é um tema
  - A área do tema (frontend / adminhtml), o vendor e o nome 'frontend/LucasCalazans/default'
  - O caminho do tema, especificado pela variável \_\_DIR\_\_ do PHP que retorna o caminho absoluto

- O arquivo 'theme.xml' serve para especificar o titulo do tema (através da tag \<title>) e se ele vai herdar as características de outro tema (através da tag \<parent>).

#### Arquivos estáticos

O tema também pode possuir o diretório 'web', onde ficam os arquivos estáticos. Nesse diretório, o Magento espera que os arquivos 'less' estejam no caminho ' css > source '

No diretório 'source', o arquivo '\_extend.less' é obrigatório, ele tem a função de estender os estilos padrões. Para deixar o código mais limpo e organizado, nele podem ser feitas as importações de outros arquivos 'less'.
  
_Obs.: para que as mudanças sejam feitas, é necessário apagar os seguintes arquivos: 'cache', 'page_cache' e 'view_preprocessed' na pasta ' app > var '. E o arquivo 'frontend' na pasta ' app > pub > static '_

## XML

Quando trabalhamos com Layout XML, tratamos páginas como handles, sendo que cada página pode ter 1 ou mais handles. Segue uma lista com os mais conhecidos:

- default: todas as páginsa
- cms_index_index: página inicial
- catalog_category_view: categoria
- catalog_product_view: produto
- checkout_cart_index: carrinho
- checkout_index_index: checkout

### Exemplo de adição de bloco

```
<?xml version="1.0"?>
<page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
    <body>
        <referenceContainer name="content">
            <block class="Magento\Framework\View\Element\Text" name="simple.text.example" before="-">
                <arguments>
                    <argument name="text" xsi:type="string">It is a block example</argument>
                </arguments>
            </block>
        </referenceContainer>
    </body>
</page>
```
No exemplo acima, estamos adicionando um bloco de texto na página inicial através do arquivo cms_index_index.

Cada handle fica dentro da pasta "layout" que, por sua vez, fica na pasta com o código do módulo responsável pelo handle. Ou seja, se você estiver trabalhando com o handle checkout_index_index, deve colocá-lo na pasta "layout" e esse na pasta Magento_Checkout

### handles especiais

Alguns handles agem em todas as páginas ao mesmo tempo, como é o caso do default.xml. Esse handle é muito usado para customização do header e do footer

### Block

É com um bloco que falamos para o Magento renderizar um phtml (arquivo com instruções php e html), sendo que esse phtml pode chamar métodos disponíveis em uma classe PHP através da propriedade class

Quando o Magento encontra dois blocos com o mesmo nome, ele irá sobrescrever o antigo pelo último carregado (o que criamos). Para que isso não aconteça, podemos selecionar o bloco através da tag \<referenceBlock>

Podemos fazer uma série de alterações com o referenceBlock. Por exemplo:

- Alterar o template

~~~
<referenceBlock name="simple.block.example" template="Magento_Theme::html/different-template.phtml" />
~~~

- Adicionar novos blocos

~~~
<referenceBlock name="simple.block.example">
  <block name="child.block" template="Magento_Theme::html/child-template.phtml" />
</referenceBlock>
~~~

### Container

Containers são úteis para o agrupamento de blocos ou até mesmo outros containers. Com ele podemos criar elementos HTML simples direto pelo XML, observe o exemplo:

~~~
<container name="footer" as="footer" label="Page Footer" htmlTag="div" htmlClass="footer content">
~~~

Assim como nos blocos, também possuimos a tag \<referenceContainer>. Se, por exemplo, quisermos adicionar um novo bloco no header.container, o código ficaria assim:

~~~
<referenceContainer name="header.container">
  <block name="header.user.information" template="Magento_Customer::header/user-info" after="-" />
</referenceContainer>
~~~

### before / after

Com os atributos before e after podemos informar onde ficará o bloco/container. Veja o exemplo:

~~~
<referenceContainer name="content">
    <block class="Magento\Framework\View\Element\Text" name="simple.text.example" before="-">
        <arguments>
            <argument name="text" xsi:type="string">It is a block example</argument>
        </arguments>
    </block>
</referenceContainer>
~~~

Perceba que, nesse caso, estamos selecionando o container com o nome 'content' e, dentro dele, inserindo um bloco antes de todos os outros elementos. Isso é feito através do before="-"

~~~
<referenceContainer name="content">
    <block name="cart.items.info" after="simple.text.example" template="Magento_Checkout::cart/items-info.phtml" />
</referenceContainer>
~~~

Nesse outro exemplo, estamos criando um bloco e inserindo ele após o bloco criado anteriormente "simple.text.example"

### move

A tag \<move> é responsável por mover algum elemento. Para que ela funcione, é necessario informar o 'element', que é o elemento a ser alterado (tanto bloco como container) e o 'destination', que é o destino

~~~
<move element="copyright" destination="footer-container" before="-" />
~~~

### remove

Para removermos blocos ou containers de uma página basta definirmos remove como true. Observe:

~~~
<referenceContainer name="header.container" remove="true" />
~~~

### Anotações gerais
  
1\. Dentro da tag \<argument> podemos especificar o tipo de entrada através do xsi:type="string/number/etc"\

## Módulos
  
Um módulo pode ser instalado manualmente ou através do composer pelo comando 'composer require'. De maneira manual, o download deve ser colocado no caminho ' app > code ' dentro de uma pasta com o nome do vendor. Após a instalação via composer ou manual, deve ser feito os seguintes passos:
  
1. sudo -u www-data bin/magento module:enable (nome do módulo)

2. sudo -u www-data bin/magento setup:upgrade
  
Um módulo possui dois arquivos obrigatórios: 'registration.php' e 'module.xml'
  
- O arquivo 'registration.php' serve para registrar o módulo, informando seu nome.

- O arquivo 'module.xml' fica dentro da pasta 'etc' e serve para especificar o titulo do módulo (através da tag  \<module name="nome">)
  
### Anotações
  
1. O Magento_Theme possui o arquivo 'default.xml', que é responsável pela renderização dos templates em todas as páginas
  
2. Em Magento_Cms temos o arquivo cms_index_index.xml, que é responsável pela customização da página inicial

## Anotações gerais
  
1. Customizações não devem ser feitas diretamente nos arquivos internos do Magento. Ao invés, cria-se uma pasta do arquivo do tema com o mesmo nome do módulo que se quer editar. Dentro da pasta, criamos o diretório 'layout' e, dentro deste, o arquivo 'default.xml'. Dessa forma, o Magento entende que ali existe uma "sobrescrição".

2. Primeiro o Magento carrega seus arquivos internos, depois sobrescreve com as customizações feitas na pasta do tema.

## Menus no Backoffice (Admin)

**Conteúdo > Configuração:** aqui podemos, por exemplo, definir qual será o tema de uso no Magento

**Conteúdo > Bloco:** permite a criação de blocos

## Layout

O Magento é formado, basicamente, por Layout, Container e Blocos.

<p align="center" width="250">
  <img src="https://devdocs.magento.com/common/images/layouts_block_containers_defn21.png" width=950">
</p>

(1) Layouts representam a estrutura da página através de um arquivo XML que identifica todos os containers e blocos <br>
(2) Containers atribuem a estrutura do conteúdo a página. Exemplo de containers: header, main, footer, sidebar <br>
(3) Blocos representam os componentes inseridos dentro dos containers. Os blocos usam templates para gerar o HTML. Exemplos de blocos são: minicart, lista de categorias, lista de produtos, etc. <br>
                                                                                                     
## Referências

- https://calazanslucas.medium.com/magento-2-guia-de-sobrevivencia-no-frontend-parte-1-76fe6d2ffe4e
- https://calazanslucas.medium.com/magento-2-guia-de-sobreviv%C3%AAncia-no-front-end-parte-2-83b9db02a4b4
