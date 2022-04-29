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

**pasta do projeto > app > design > frontend:** aqui é criada a pasta com o nome do tema. Essa pasta possui dois arquivos obrigatórios, sendo eles: 'registration.php' e 'theme.xml'.

- O arquivo 'registration.php' serve para registrar o tema, informando seu caminho.

- O arquivo 'theme.xml' serve para especificar o titulo do tema (através da tag \<title>) e se ele vai herdar as características de outro tema (através da tag \<parent>).

#### Arquivos estáticos

O tema também pode possuir o diretório 'web', onde ficam os arquivos estáticos. Nesse diretório, o Magento espera que os arquivos 'less' estejam no caminho ' css > source '

No diretório 'source', o arquivo '\_extend.less' é obrigatório, ele tem a função de estender os estilos padrões. Para deixar o código mais limpo e organizado, nele podem ser feitas as importações de outros arquivos 'less'.
  
_Obs.: para que as mudanças sejam feitas, é necessário apagar os seguintes arquivos: 'cache', 'page_cache' e 'view_preprocessed' na pasta ' app > var '. E o arquivo 'frontend' na pasta ' app > pub > static '_

## XML

### Anotações gerais
  
1\. Dentro da tag \<argument> podemos especificar o tipo de entrada através do xsi:type="string/number/etc"\
  
2\. Usamos a tag \<referenceBlock> para chamar um bloco já existente no Magento e fazer a customização
  
3\. A tag \<referenceContainer> faz referencia a containers
  
4\. A tag \<move> é responsável por mover algum elemento. Preciso passar o 'element' e o 'destination'

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

| Menu | Descrição |
| --- | --- |
| Conteúdo > Configuração | Configurações do tema |
| Conteúdo > Bloco | Permite a criação de blocos |

## Layout

O Magento é formado, basicamente, por Layout, Container e Blocos.

<p align="center" width="250">
  <img src="https://devdocs.magento.com/common/images/layouts_block_containers_defn21.png" width=950">
</p>

(1) Layouts representam a estrutura da página através de um arquivo XML que identifica todos os containers e blocos <br>
(2) Containers atribuem a estrutura do conteúdo a página. Exemplo de containers: header, main, footer, sidebar <br>
(3) Blocos representam os componentes inseridos dentro dos containers. Os blocos usam templates para gerar o HTML. Exemplos de blocos são: minicart, lista de categorias, lista de produtos, etc. <br>
