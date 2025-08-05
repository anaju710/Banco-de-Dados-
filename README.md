# Banco-de-Dados-

>O que é um Banco de Dados relacional?

é um tipo de sistema de gerenciamento de banco de dados que organiza dados em tabelas com linhas e colunas, estabelecendo relações entre os dados através de chaves. Essa estrutura facilita a busca, filtragem e análise de informações interconectadas.Exemplos de bancos de dados relacionais incluem MySQL, PostgreSQL, SQL Server, Oracle Database e MariaDB.

Exemplos de uso:

Gerenciamento de pedidos: Rastrear pedidos, produtos e clientes.

Sistemas financeiros: Controlar transações, contas e saldos.

Sistemas de gestão de estoque: Monitorar produtos, quantidades e movimentações.

Sistemas de gerenciamento de relacionamento com clientes (CRM): Armazenar informações sobre clientes e interações. 

![banco de dados ralacional ](https://consultabd.wordpress.com/wp-content/uploads/2019/08/img_relacional-1.jpg)

>O que é um Banco de Dados não relacional?

Um banco de dados não relacional, também conhecido como NoSQL (Not Only SQL), é um tipo de sistema de gerenciamento de banco de dados que não utiliza o modelo tradicional de tabelas com linhas e colunas para armazenar dados, como os bancos de dados relacionais. Em vez disso, eles empregam modelos de dados mais flexíveis e adaptáveis, como chave-valor, documentos, colunas largas ou gráficos, para lidar com grandes volumes de dados não estruturados ou semiestruturados. 

Exemplos de uso:

Armazenamento de perfis de usuários:
Um banco de dados de documentos pode armazenar informações de perfil com diferentes campos para cada usuário, sem a necessidade de um esquema rígido. 

Caches de alta performance:
Um banco de dados de chave-valor pode armazenar dados em cache para melhorar a velocidade de acesso. 

Análise de dados em tempo real:
Bancos de dados de colunas podem ser usados para análises rápidas de grandes volumes de dados. 

Redes sociais:
Bancos de dados de grafos podem armazenar e analisar as relações entre usuários e conteúdo. 

Monitoramento de dispositivos IoT:
Bancos de dados de séries temporais podem armazenar e consultar dados de sensores ao longo do tempo.

![banco de dados relacional e não relacional](https://hermes.dio.me/articles/cover/f029222d-afc1-4fb2-b010-1a463aae0ae7.png)

>O que é Normalização e seu objetivo?

Normalização é o processo de organização de dados em um banco de dados. Isso inclui a criação de tabelas e o estabelecimento de relações entre essas tabelas de acordo com as regras projetadas para proteger os dados e tornar o banco de dados mais flexível, eliminando a redundância e a dependência inconsistente,é utilizada cada vez mais como um meio para se alcançar a redução de custo da produção e do produto final, mantendo ou melhorando sua qualidade.

![normalização objetivos](https://abnt.org.br/wp-content/uploads/2023/11/Mj4Bhcl6q0LNqGI5tPBYpZ5Nq1MaMdNu2k99VXbL-1.png)





| Pedido_id | Cliente_nome | Cliente_endereço  | Produto_id | Produto_nome  | Quantidade | Preço total |  
|-----------|--------------|-------------------|------------|---------------|------------|-------------|
| 1         | João Silva   | Rua A,123         | 10         | Caneta        | 2          | 4,00        |   
| 1         | João Silva   | Rua A,123         | 11         | Lápis         | 1          | 2,00        |   
| 2         | Maria Souza  | Av.B,456          | 10         | Caneta        | 5          | 10,00       |   



# Tabela normalizada

1. Tabela cliente

|   | ID do Cliente  |   | Nome        |   | Endereço                              |   | Número de endereço  |   
|---|----------------|---|-------------|---|---------------------------------------|---|---------------------|
|   | 1              |   | Ana Clara   |   | Rua Tenente Nicolau Maffei            |   | 505                 |   
|   | 2              |   | Maria Clara |   | Avenida Coronel José Soares Marcondes |   | 2169                |   


2. Tabela produto

| Produto_id |   | Nome produto |   | Preço Unitário |   
|------------|---|--------------|---|----------------|
| 1          |   | Camisa       |   | 50,00          |   
| 2          |   | Calça        |   | 120,00         |   
| 3          |   | Tênis        |   | 200,00         |   

3.Tabela pedido 

| Pedido_id |   | Cliente_id |   | Produto_id |   | Quantidade  | 
|-----------|---|------------|---|------------|---|-------------|
| 1         |   | 1          |   | 1          |   | 2           |   
| 1         |   | 1          |   | 2          |   | 1           |   
| 2         |   | 2          |   | 3          |   | 1           |   
| 3         |   | 1          |   | 1          |   | 1           |   


{
  "clientes": [
    {
      "ClienteID": 1,
      
      "Nome": "João Silva",

      
      "Endereco": "Rua A, 123"
      
    },
    {
      "ClienteID": 2,
      
      "Nome": "Maria Oliveira",
      
      "Endereco": "Avenida B, 456"
    }
    
  ],
  "produtos": [
  
    {
      "ProdutoID": 1,
      
      "NomeProduto": "Camiseta",
      
      "PrecoUnitario": 50.00
      
    },
    {
      "ProdutoID": 2,
      
      "NomeProduto": "Calça",
      
      "PrecoUnitario": 120.00
      
    },
    {
      "ProdutoID": 3,
      
      "NomeProduto": "Tênis",
      
      "PrecoUnitario": 200.00
      
    }
  ],
  "pedidos": [
  
    {
      "PedidoID": 1,
      
      "ClienteID": 1,

      "Itens": [
      
        {
          "ProdutoID": 1,
          
          "Quantidade": 2
          
        },
        {
        
          "ProdutoID": 2,
          
          "Quantidade": 1
        }
      ]
      
    },
    {
      "PedidoID": 2,
      
      "ClienteID": 2,
      
      "Itens": [
      
        {
          "ProdutoID": 3,
          
          "Quantidade": 1
          
        }
      ]
    },
    {
      "PedidoID": 3,
      
      "ClienteID": 1,
      
      "Itens": [
      
        {
          "ProdutoID": 1,
          
          "Quantidade": 1
          
          
      ]
    }
  ]
}


{

  A estrutura JSON elimina a necessidade de normalização porque armazena dados de forma hierárquica, agrupando informações relacionadas (como cliente, pedido e produto) em um único documento. Isso reduz a redundância, já que os dados são referenciados por IDs, e facilita consultas mais rápidas, pois não é necessário fazer junções complexas entre tabelas. 
