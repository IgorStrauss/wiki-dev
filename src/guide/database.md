# Databases

## PostgreSQL

**PostgreSQL** é um banco de dados relacional de código aberto amplamente reconhecido por sua conformidade com os padrões SQL e seu suporte a recursos avançados, como consultas complexas, transações ACID, e extensibilidade. Ele oferece suporte a índices avançados, funções definidas pelo usuário, e tipos de dados personalizados, o que o torna altamente personalizável e adequado para sistemas que exigem alta integridade de dados e consultas complexas. Além disso, o PostgreSQL suporta dados JSON nativamente, o que permite trabalhar com dados semiestruturados, integrando-se bem em ambientes híbridos.

**Destaques**:

- Suporte robusto a transações e conformidade com ACID.
- Funcionalidades de extensão e customização.
- Índices avançados, como GIN e GiST, úteis para pesquisas de texto e dados geoespaciais.
- Escalabilidade vertical (performance em instâncias maiores) e horizontal (particionamento).

**Casos de uso comuns**:
- Sistemas financeiros
- Análises geoespaciais
- Aplicativos que exigem alta integridade de dados.

## SQL Server

**Microsoft SQL Server** é uma plataforma de banco de dados relacional comercial, desenvolvida pela Microsoft, com um forte foco em soluções empresariais. Ele oferece suporte nativo a transações ACID, processamento analítico (OLAP) e integração com o ecossistema da Microsoft, como .NET e Azure. O SQL Server é conhecido por suas ferramentas de administração, como o SQL Server Management Studio (SSMS), que facilitam o gerenciamento de instâncias, e o SQL Server Integration Services (SSIS), que oferece suporte robusto a processos ETL.

**Destaques**:

- Suporte a OLAP, Data Warehousing e Business Intelligence (BI).
- Integração nativa com ferramentas da Microsoft (Power BI, Azure).
- Recursos avançados de segurança e criptografia de dados.
- Suporte a containers e execução em ambientes Linux, além do tradicional Windows.

**Casos de uso comuns**:
- Grandes empresas
- Data warehouses
- Sistemas transacionais corporativos e integração com a suíte Microsoft.

## MySQL

**MySQL** é um dos bancos de dados mais populares do mundo, conhecido por sua simplicidade, escalabilidade e forte desempenho em ambientes de web, como backends de sites e aplicações SaaS. Ele oferece suporte a transações ACID com o mecanismo de armazenamento InnoDB e permite otimizações de performance através de índices e consultas ajustáveis. Embora seja um banco de dados relacional, MySQL também oferece suporte básico para JSON, o que o torna adaptável a aplicações mais modernas.

**Destaques**:

- Desempenho alto em leituras e grande capacidade de escalabilidade.
- Suporte a replicação master-slave e master-master para alta disponibilidade.
- Foco em simplicidade e fácil integração com linguagens populares como PHP e Python.
- Ampla comunidade de suporte e documentação.

**Casos de uso comuns**:
- Aplicações web
- E-commerce
- Startups e aplicativos de pequena e média escala.

## SQLite

**SQLite** é um banco de dados leve, embutido em aplicações e baseado em arquivos, amplamente usado em sistemas onde simplicidade e portabilidade são mais importantes do que desempenho ou escalabilidade. Ele não é um banco de dados cliente-servidor tradicional, pois armazena os dados em um único arquivo no sistema de arquivos, o que o torna ideal para aplicações móveis, desktop e prototipagem rápida. Além disso, não requer configuração de um servidor de banco de dados.

**Destaques**:

- Banco de dados embutido, zero configuração, e pequeno em tamanho.
- Suporte a transações ACID e consultas SQL completas.
- Extremamente rápido para operações de leitura e aplicações com baixo volume de escrita.
- Usado em sistemas como navegadores web e aplicações mobile.

**Casos de uso comuns**:
- Aplicações mobile (Android e iOS)
- Prototipagem
- Sistemas embarcados, e armazenamento local em browsers.

## MongoDB

**MongoDB** é um banco de dados NoSQL orientado a documentos que armazena dados no formato JSON/BSON. É amplamente utilizado em aplicações que lidam com grandes volumes de dados semiestruturados e que requerem alta escalabilidade horizontal. MongoDB permite uma abordagem flexível ao esquema, o que facilita a adaptação a mudanças nos dados. Além disso, seu suporte a replicação e particionamento torna o MongoDB adequado para aplicativos distribuídos e de alta disponibilidade.

**Destaques**:

- Armazenamento de dados em formato JSON/BSON, permitindo flexibilidade de esquema.
- Suporte nativo a sharding (particionamento horizontal) para escalabilidade massiva.
- Focado em alta disponibilidade com replicação automática e failover.
- Índices poderosos e consultas flexíveis para trabalhar com grandes volumes de dados.

**Casos de uso comuns**:
- Aplicações de big data
- Sistemas de gerenciamento de conteúdo
- E-commerce e aplicações que exigem dados flexíveis.


## Cassandra

**Apache Cassandra** é um banco de dados NoSQL distribuído e escalável, otimizado para grandes volumes de dados distribuídos geograficamente. Ele utiliza uma arquitetura sem um ponto único de falha, o que garante alta disponibilidade e tolerância a falhas em grandes infraestruturas. O Cassandra oferece forte escalabilidade horizontal e suporte a replicação multi-data center, tornando-se ideal para aplicativos de alta exigência em termos de performance e disponibilidade.

**Destaques**:

- Escalabilidade horizontal quase infinita, ideal para grandes volumes de dados.
- Arquitetura distribuída sem ponto único de falha, garantindo alta disponibilidade.
- Suporte a replicação em múltiplos data centers, permitindo recuperação de desastres.
- Modelagem baseada em tabelas amplas, focada em performance de escrita e leituras rápidas.

**Casos de uso comuns**:
- Sistemas de monitoramento em tempo real
- Redes sociais
- Sistemas de recomendação e grandes infraestruturas de IoT.