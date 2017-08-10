---
layout: post
title:  "Iniciando com Big Data"
date:   2017-08-09 23:09:20 -0300
categories: big data, data science, basics
---

Para quem está chegando agora ou ainda não teve oportunidade de conhecer as **motivações e ferramentas** mais comuns utilizadas neste mundo de *big data*, vou tentar passar aqui uma visão geral. A verdade é que são tantas ferramentas que fica até difícil distinguí-las de pokemons :) É sério!! Depois de ler essa matéria, faça o teste [Pokemon ou *Big Data*](https://pixelastic.github.io/pokemonorbigdata/).

*`Big Data`* é um termo bastante utilizado atualmente e ligado diretamente ao volume de dados a ser processado e analisado (algumas definições podem ser vistas nesse outro artigo [O que é *Big Data*](http://www.semantix.com.br/o-que-e-big-data/)). Para o processamento e análise destes dados recorremos à ciência de dados.

*`Data Science`* (Ciência de Dados) é uma prática que envolve métodos científicos, processos e sistemas para extrair conhecimento ou *insights* tanto de dados estruturados como de não-estruturados. É um conceito que unifica estatística, análise de dados e métodos relacionados com a finalidade de entender e analisar fenômenos através de seus dados. Este conceito emprega técnicas e teorias de diversas áreas de conhecimento da matemática, estatística, e ciência da computação (mais especificamente de subdomínios de aprendizado de máquina, classificação, clusterização, mineração de dados, e visualização).

![alt](../assets/img/2017-07-11@06.49.15-mindmap-datascience.png)

Além de conhecimentos matemáticos, *data science* também requer conhecimentos em ferramentas para análise de dados e também programação. Entre as ferramentas para realizar estas análises estão o famoso SPSS (adquirida pela IBM em 2009), R/RStudio, Jupyter e Zeppelin, entre outras. No campo da programação está a conhecida linguagem Java, Scala e Clojure, que utilizam a JVM para sua execução. A linguagem Python também é muito útil pois é flexível e permite agilidade no desenvolvimento. As linguagens java, scala e python podem ser utilizadas com o Spark, um framework para processamento de dados em grande escala. Muitas das ferramentas podem ser utilizadas gratuitamente, e são mais facilmente instaladas em sistemas operacionais linux.

Após a análise é necessário demonstrar resultados através de relatórios, gráficos, *dashboards* e/ou modelos gerados. 

Com estas simples explicações podemos perceber que *data science* requer uma certa bagagem de conhecimentos diversos.

Ao tratar com *big data* já surgem dois desafios: capacidade de armazenamento e velocidade de processamento. Ambos nos conduzem a uma limitação computacional onde a velocidade de I/O (gravação e leitura) de discos não acompanhou a evolução dos processadores, e mesmo para o melhor processador é difícil dar vazão a grandes quantidades de informação sozinho. Estes dois desafios podem ser resolvidos utilizando-se uma arquitetura onde os dados estão distribuídos e próximos a unidades de processamento (a leitura de um grande arquivo a partir de uma máquina leva muito tempo comparando-se com a leitura deste mesmo arquivo num ambiente distribuído ao ser lido por diversas máquinas).

A tecnologia compatível com a arquitetura citada é o *`HDFS`*, que é um *filesystem* distribuído, inspirado no GFS (*Google File System*), e executado em *nodes* utilizando *hardware commodity*. Ele não foi criado para ser transacional, ou seja, receber muitas requisições de leitura e escrita, mas para realizar única gravação e diversas leituras. O objetivo é que os *nodes* com *HDFS* sejam utilizados como RAIN (Redundant Array of Independent Nodes) para armazenar dados a serem processados por diversos componentes do ecossistema *HADOOP*.

*`Hadoop`* é um projeto *open-source* da Apache que possibilita o processamento distribuído de grandes volumes de dados por um conjunto de máquinas (*cluster*) usando modelos de programação simples. O projeto é desenhado de forma a ser escalável desde poucos servidores até milhares de máquinas, onde cada uma oferece processamento e armazenamento de dados. Ele contém os seguintes módulos:

* Hadoop Common: o componente base que suporta as demais ferramentas.
* HDFS (*Hadoop Distributed File System*): sistema de arquivos distribuídos, escalável, tolerante a falhas e de baixo custo.
* Hadoop YARN: *framework* para agendamento de *jobs* e gerenciamento de recursos no *cluster*.
* Hadoop MapReduce: sistema baseado no Yarn para processamento paralelo.

As distribuições *hadoop* disponíveis são Cloudera (que possui o módulo de segurança mais maduro), Hortonworks e MapR, onde as ferramentas mais comuns do ecossistema estão representadas na imagem abaixo:

![alt](../assets/img/2017-07-13@16.42.16-hadoop.png)

Cada distribuição tem alguns módulos específicos como o Cloudera Manager, HUE, Impala e Sentry na distribuição Cloudera, e o Ambari, Tez, Knox e Ranger na distribuição Hortonworks.

O gráfico acima representa a distribuição Cloudera, com suas ferramentas e finalidades, e nele podemos ver o `YARN` (*Yet Another Resource Manager*) que gerencia os recursos do cluster, recebendo requisições e submetendo-as aos recursos disponíveis. Outra ferramenta que atua como base para os demais serviços é o `Sentry`, módulo de segurança que funciona com o Kerberos (base da segurança em um cluster *hadoop*).

Entre os serviços de **integração**, existem:

* `Sqoop`- ferramenta para transferência (entrada e saída) de informações entre o *hadoop* e fontes estruturadas, como bases de dados relacionais;
* `Flume`- serviço distribuído, com arquitetura flexível baseada em *streaming*, para coleta, agregação e movimentação de grandes quantidades de dados;
* `Kafka`- plataforma distribuída de streamings, que funciona como um *checkpoint* de dados, para montagem de *pipelines* entre sistemas ou aplicações.

Quando falamos em **armazenamento** das informações no *stack* Cloudera, temos:

* `HDFS` - o próprio *filesystem*;
* `HBase` - a base de dados não-relacional *open source* distribuída que funciona em conjunto com o HDFS, baseada no Bigtable do Google, e indicada para grandes volumes de informações;
* `Kudu` - a base de dados relacional complementar ao HDFS e ao HBase que permite rápido acesso aos dados, reduzindo consideravelmente a latência de ferramentas como o Spark e Impala.

Finalmente, para **processamento e análise de dados**, temos ferramentas como:

* `Hive` - ferramenta com uma camada de abstração SQL que facilita leitura, escrita e o gerenciamento de dados em grandes *datasets* no HDFS;
* `MapReduce` - framework que opera sobre pares (chave/valor) para processar grandes quantidades de dados em grandes *clusters*, dividindo os dados em partes que são processadas paralelamente;
* `Impala` - database analítica que consulta dados armazenados no HDFS e HBase, que utiliza os mesmos metadados, sintaxe SQL e driver ODBC utilizado para o Hive.
* `Solr` - ferramenta tolerante a falhas, escalável e confiável, que permite indexação de textos e buscas avançadas, oferecendo ainda APIs baseadas em REST que permite integração com praticamente qualquer linguagem de programação;
* `Spark` - framework para desenvolvimento de programas (em scala ou python) para processamento paralelo distribuído em larga escala que é formado por diversos módulos (Core, SQL, Streaming, MLlib, GraphX).

Todas essas técnicas, tecnologias e ferramentas podem ser amplamente utilizadas em diversos mercados (financeiro, telecom, seguros, governo, comércio e serviços) suportando diversos tipos de aplicações como identificação de fraudes, classificações de clientes, predições de consumo, buscas textuais e outras análises.
