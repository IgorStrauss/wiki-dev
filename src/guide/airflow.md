# Airflow

**Apache Airflow** é uma ferramenta open-source utilizada para a orquestração de workflows e pipelines de dados.

Seu principal foco é permitir a automação de processos complexos que envolvem múltiplos passos de **ETL (Extração, Transformação e Carga)** e outras tarefas agendadas de forma escalável e flexível.

Airflow é amplamente utilizado em pipelines de dados porque oferece uma abordagem declarativa para a definição de fluxos de trabalho, utilizando DAGs (Directed Acyclic Graphs), o que permite maior controle e monitoramento sobre as execuções.

##  Airflow em Pipelines de Dados

- Orquestração Escalável e Flexível: O Airflow permite que fluxos de trabalho sejam orquestrados de maneira escalável, controlando desde pipelines simples até arquiteturas de dados mais complexas. Ele oferece suporte para integração com diversas tecnologias de dados, como Hadoop, Spark, Hive, BigQuery, AWS, GCP e outros serviços em nuvem, o que o torna ideal para uma variedade de ambientes.

- Definição de Workflows com Python: Airflow usa Python para definir workflows, o que é uma grande vantagem, pois torna os fluxos de trabalho altamente customizáveis e acessíveis para desenvolvedores e engenheiros de dados. Cada tarefa dentro do DAG pode ser configurada, agendada e monitorada com base em eventos ou triggers, oferecendo grande flexibilidade no controle de processos de ETL.

- Gerenciamento de Dependências e Retentativas: Um dos maiores pontos fortes do Airflow é a capacidade de definir dependências explícitas entre tarefas. Isso permite que uma tarefa só seja executada quando todas as dependências anteriores tiverem sido concluídas com sucesso. Caso ocorra uma falha, o Airflow também oferece retentativas automáticas com gerenciamento de falhas, ajudando a garantir a execução consistente do pipeline.

- Monitoramento e Logging Detalhado: O Airflow fornece uma interface web que permite monitorar, gerenciar e rastrear a execução dos workflows. Os logs detalhados de cada tarefa tornam mais fácil o diagnóstico e a resolução de falhas durante a execução dos pipelines de dados. O sistema de monitoramento oferece insights em tempo real sobre o status das tarefas, possibilitando um acompanhamento contínuo dos processos.

- Suporte a Execuções Paralelas e Scheduling: Airflow oferece suporte a execuções paralelas, o que melhora a eficiência do processamento de grandes volumes de dados, uma característica fundamental em pipelines de Big Data. O agendador embutido permite configurar a periodicidade das execuções dos workflows, desde execuções em tempo real até execuções em janelas de tempo maiores, como diárias ou semanais.

- Conectores para Serviços em Nuvem e Tecnologias de Big Data: O Airflow tem suporte nativo a uma ampla gama de conectores para serviços como AWS, Google Cloud, e Azure, além de integrações com ferramentas de dados como Spark, Hive, e Snowflake. Isso facilita a orquestração de pipelines em ambientes heterogêneos, onde diferentes sistemas de processamento de dados estão em uso.

## Versão 2.3 do Airflow

- **Scheduler HA (High Availability)**: O Airflow agora oferece suporte nativo a Alta Disponibilidade no Scheduler, um grande avanço para ambientes de produção. Anteriormente, o agendador era um ponto único de falha em muitas implementações, mas a nova versão garante que múltiplas instâncias do agendador possam operar simultaneamente para maior resiliência e disponibilidade.

- **Melhorias no TaskFlow API**: A nova versão traz aprimoramentos à TaskFlow API, introduzida em versões anteriores, que simplifica a definição e execução de tarefas dentro do DAG. Agora, os pipelines podem ser definidos de forma ainda mais declarativa, facilitando a leitura e manutenção dos fluxos de trabalho.

- **Suporte Melhorado para Múltiplos Schedulers**: A introdução de múltiplos schedulers permite que grandes volumes de DAGs sejam agendados de maneira eficiente. Com esta melhoria, os pipelines podem ser executados em menor tempo, especialmente em ambientes com cargas pesadas de workflows.

- **Task Groups e Visão Hierárquica dos DAGs**: A funcionalidade de Task Groups melhora a organização e visualização dos DAGs, agrupando tarefas relacionadas e permitindo uma visualização mais limpa e organizada, especialmente em fluxos de trabalho complexos. Isso é útil para empresas que gerenciam DAGs extensos com centenas de tarefas.

- **Aprimoramentos em Alertas e Notificações**: O Airflow agora oferece uma infraestrutura de notificações mais robusta para gerenciar alertas em tempo real. Com a nova versão, é possível personalizar facilmente alertas para diferentes condições de falha ou sucesso de tarefas, usando integrações com plataformas como Slack e e-mails customizados.

- **DAG Versioning (Controle de Versão de DAGs)**: A nova versão introduziu suporte a DAG Versioning, que facilita o rastreamento de mudanças nos workflows ao longo do tempo. Isso permite que engenheiros de dados visualizem e retornem a versões anteriores de DAGs, garantindo mais controle sobre as modificações em ambientes de produção.

- **Melhorias no Kubernetes Executor**: Para equipes que utilizam Kubernetes para escalabilidade, a nova versão do Airflow melhorou a integração com o Kubernetes Executor, tornando mais fácil a criação de ambientes altamente escaláveis e dinâmicos para execução de tarefas.

O Apache Airflow continua a ser uma das melhores opções para orquestração de pipelines de dados, com forte flexibilidade e escalabilidade. A nova versão introduz aprimoramentos significativos em termos de alta disponibilidade, organização de workflows e integração com tecnologias modernas como Kubernetes. As inovações em recursos como o Scheduler HA, TaskFlow API e DAG Versioning consolidam o Airflow como uma ferramenta robusta e eficiente para cenários de produção e ambientes distribuídos, oferecendo mais controle e resiliência em pipelines críticos de dados.