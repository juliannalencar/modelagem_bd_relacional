# Modelagem Banco de Dados Relacional - AuraBella
Este projeto educacional foi desenvolvido durante a trilha de Dados do programa Desenvolve 2024, focando na criação de um banco de dados relacional para processos de ***vendas***, ***gestão de estoque*** e ***pontuação de clientes*** na **AuraBella**, uma empresa fictícia do setor de cosméticos. Será aberta uma nova franquia que precisa de um sistema robusto para gerenciamento de processos e armazenamento de dados. Durante este projeto, foi desenvolvido os modelos *conceitual*, *lógico* e *físico* deste banco de dados relacional.
<br>

## Fluxo de Processos na AuraBella
A distribuição de produtos da AuraBella para as franquias é feita por Centros de Distribuição (CD). Após o recebimento das mercadorias, estas são registradas no estoque através de um processo de entrada, utilizando documentos como notas fiscais para detalhar os itens recebidos. O estoque é então atualizado para refletir os novos itens.

Os processos de compra e de acumulação de pontos estão diretamente associados aos clientes, que precisam estar cadastrados no sistema com todas as informações relevantes. Cada compra deve ser associada a um cliente específico e a pelo menos um produto.

Quando uma compra é concluída, pontos são atribuídos ao cliente, que podem ser usados como desconto em futuras compras dentro de um prazo determinado. Simultaneamente, o sistema atualiza o estoque para reduzir as quantidades dos itens vendidos.
<br>

## Modelo Conceitual 
A análise do fluxo de processos permitiu identifucar as entidades e atributos essenciais para a estruturação do banco de dados. O **modelo conceitual** apresentado a seguir ilustra essas abstraçòes, delineando as entidades, seus atributos e as relações entre eles. <br>
<br>
![Modelo Conceitual](https://i.imgur.com/dmgcykp.png)
<br>

## Descrição de Entidades
Nessa etapa, é possível entender um pouco melhor cada entidade e como elas se relacionam.<br>

* __CENTRO_DISTRIBUICAO__: <br>
Descreve o Centro de Distribução (CD) responsável por realizar a entrega de produtos. Estará diretamente relacionada as entradas de produtos.<br>
    
* __ENTRADA__: <br>
Descreve a entrada de produtos, sendo a parte identificadora da entrada, contendo as informações da entrega, como: número do documento de entrega (nota fiscal ou semelhante), data, CD e valor total da entrada. Toda entrada deve estar vinculada a um centro de distribuição.

* __ITEM_ENTRADA__: <br>
Esta entidade descreve separadamente cada item listado em uma determinada entrada. Portanto, cada ocorrência deve obrigatoriamente estar vinculado a uma entrada e um produto.

* __PRODUTO__:<br>
Descreve os produtos, sendo que cada produto deve estar vinculado a uma categoria.

* __CATEGORIA__:<br>
Descreve as categorias as quais os produtos serão vinculados. É separada em **grupo** e **subgrupo**, sendo o grupo uma característica mais geral e o subgrupo uma característica mais específica.<br>
__Exemplo__: <br>
_Grupo_ -> Perfumaria<br>
_Subgrupo_ -> Perfumaria Feminina, Perfumaria Masculina, Perfumaria Infantil

* __CLIENTE__:<br>
Descreve os clientes, que serão vinculados as compras e também as pontuações.

* __COMPRA__:<br>
Descreve as compras realizadas pelos clientes, portanto, a mesma deve estar vinculada a um cliente e também as pontuações, uma vez que a compra pode gerar uma pontuação. É o descritivo mais geral do processo, possuindo informações como cliente que realizou a compra, data, valor total e desconto (se aplicável).

* __ITEM_COMPRA__:<br>
Descreve separadamente cada item listado em uma determinada compra, deve obrigatoriamente estar vinculado a uma compra e um produto.

* __PONTUACAO__:<br>
Descreve as pontuações vinculadas a cada cliente a partir de suas respectivas compras, a pontuação está vinculada tanto ao cliente, quanto a compra que gerou essa pontuação.
Também registra o tipo de movimentação realizada sobre os pontos, tendo em vista que os pontos podem ser gerados e descontados em outras compras, bem como a data de movimentação de cada pontuação.

* __ESTOQUE__:<br>
Descreve o estoque, listando os produtos em estoque e suas respectivas quantidades, deve estar relacionado a produtos.

## Modelo Lógico
Baseado no modelo conceitual, desenvolvemos o __modelo lógico__, que transforma entidades em tabelas e atributos em campos. Conforme práticas de normalização, os atributos compostos do modelo conceitual são distribuídos em tabelas distintas para simplificar a estrutura e evitar a superlotação de campos em uma única tabela, como ilustrado na imagem abaixo. <br>
<br>
![Modelo Lógico](https://i.imgur.com/BX0olvL.png)
<br>

## Modelo Físico
Finalizando, apresentamos o __modelo físico__ abaixo. Este modelo detalha os tipos de dados para cada coluna, estabelece as relações entre as tabelas e especifica as chaves primárias e estrangeiras de cada tabela. <br>
<br>
![Modelo Físico](https://i.imgur.com/tC5GlZd.png)
<br>

## Ferramentas utilizadas
 
 * [BrModel](http://www.sis4.com/brModelo/#google_vignette): Desenvolvimento dos modelos conceitual e lógico.
 * [SQL Power Architect](https://dbmstools.com/tools/sql-power-architect): Desenvolvimento do modelo físico.

## Autora
__Julianna Dantas Alencar Reis__ <br><br> [![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/juliannalencar/)