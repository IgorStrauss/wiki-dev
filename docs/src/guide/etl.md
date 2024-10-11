# ETL

## Dimensão Degenerada

A **dimensão degenerada** é um conceito fundamental em modelagem de dados, especialmente em ambientes de **Data Warehousing** e **ETL (Extração, Transformação e Carga)**.

Ela refere-se a uma **dimensão que não possui atributos descritivos**, ou seja, contém apenas um identificador que é essencial para o processo de análise, mas que não é suportado por informações adicionais que caracterizam uma entidade.


**Descrição**

A dimensão degenerada geralmente é **utilizada para representar fatos que são frequentemente consultados, mas que não precisam de uma tabela de dimensão separada**.

Um exemplo típico é um número de pedido ou uma referência de transação. Nestes casos, o identificador da transação pode ser tratado como uma dimensão degenerada, já que ele não precisa de informações adicionais para ser analisado.

Exemplos

**Fatos de Vendas**:
- Em um modelo de vendas, um pedido pode ser representado apenas pelo seu número. Esse número, que serve como uma chave única, pode ser classificado como uma dimensão degenerada.
Neste caso, a tabela de fatos de vendas pode ter colunas como ID_Venda, Data_Venda, Valor_Venda, e Numero_Pedido, onde Numero_Pedido é a dimensão degenerada.

**Fatos Financeiros**:
- Em um cenário financeiro, uma transação bancária pode ser identificada apenas por um número de transação. Novamente, esse número pode ser considerado uma dimensão degenerada se não houver necessidade de atributos descritivos adicionais.

**Necessidades de Uso**

A utilização de dimensões degeneradas é vantajosa quando:

**Simplicidade**: O modelo de dados é simplificado, pois não é necessário criar e manter uma tabela de dimensão separada para informações que não são relevantes para a análise.

**Performance**: Reduz a complexidade das junções (joins) entre tabelas, melhorando o desempenho das consultas.

**Espaço**: Minimiza o uso de espaço de armazenamento, uma vez que não há necessidade de armazenar dados duplicados em uma tabela de dimensão separada.

**Comparativo com Outras Dimensões**

**Dimensões Normais**:
- Dimensões tradicionais possuem atributos descritivos (como Nome_Produto, Categoria_Produto) e permitem análises detalhadas. As dimensões degeneradas, por outro lado, têm um uso mais restrito e focado em identificadores.

**Dimensões Junk**:
- Dimensões junk são usadas para agrupar atributos que não se encaixam bem em dimensões normais. Por exemplo, um conjunto de flags ou indicadores que podem ser usados para filtrar dados. Enquanto as dimensões degeneradas lidam apenas com identificadores únicos, as junk dimensões contêm dados mais variados e podem incluir múltiplos atributos.

#### Bancos de Dados que Aceitam Dimensões Degeneradas

A implementação de **dimensões degeneradas** é suportada por muitos sistemas de gerenciamento de banco de dados (SGBDs) que são comumente utilizados em ambientes de Data Warehousing e ETL, incluindo:

**SQL Server**:
- O SQL Server é amplamente utilizado em ambientes corporativos e oferece suporte a modelos de dados dimensionais, permitindo a criação de dimensões degeneradas em tabelas de fatos.

**PostgreSQL**:
- O PostgreSQL, conhecido por sua flexibilidade e extensibilidade, é uma ótima escolha para implementar dimensões degeneradas, especialmente em sistemas que requerem complexidade de consulta e integração com outros dados.

**MySQL**:
- O MySQL, embora tradicionalmente usado para aplicações web, também pode ser configurado para suportar modelagem dimensional e permitir o uso de dimensões degeneradas.

**Oracle**:
- O Oracle Database é uma plataforma robusta que suporta modelos de dados complexos, incluindo dimensões degeneradas, facilitando a análise de grandes volumes de dados.

**MongoDB**:
- Em um contexto NoSQL, o MongoDB permite a modelagem flexível dos dados, onde dimensões degeneradas podem ser representadas como documentos com identificadores únicos.