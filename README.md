# Projeto-de-Engenharia-de-Dados-Netflix-Analytical

## Objetivo
Este projeto teve como objetivo analisar padrões de popularidade e avaliação de filmes na plataforma Netflix. Utilizando dados extraídos de arquivos CSV, buscamos identificar quais gêneros se destacam, como as avaliações variam ao longo do tempo e quais fatores influenciam a popularidade dos títulos.
<img width="982" height="426" alt="{D58E926E-7AE6-4529-BBD3-75BADA42A2EB}" src="https://github.com/user-attachments/assets/b3ff2bda-4c50-47ed-85ef-6dfd797774c9" />


## Metodologia
Os dados foram obtidos a partir de arquivos CSV armazenados no Google Cloud Storage. Criamos seis tabelas externas no BigQuery:
- Filmes: Contém o ID, título e gêneros dos filmes.
- Histórico de Avaliações: Registra o usuário, o filme avaliado, a nota e o timestamp.
- Conjunto de Elicitação: Lista de filmes sugeridos.
- Dados de Crença: Contém percepções dos usuários sobre os filmes, com previsões e certezas.
- Avaliações de Usuários Adicionais: Avaliações adicionais de outros usuários.
- Histórico de Recomendações: Mostra o histórico de recomendações feitas ao usuário.

## Origem dos Dados
Os dados foram obtidos a partir de arquivos CSV armazenados no Google Cloud Storage. Os arquivos foram referenciados nas tabelas externas criadas no BigQuery, permitindo uma análise robusta e escalável. Cada tabela foi projetada para capturar aspectos distintos do comportamento do usuário e das avaliações, formando a base para as análises no dashboard.

## Consultas SQL
Esta consulta cria uma tabela externa no BigQuery a partir de um arquivo CSV armazenado no Google Cloud Storage. Os dados são carregados diretamente do bucket, contendo informações de filmes como identificador, título e gêneros. A configuração permite ignorar o cabeçalho do arquivo e tratar possíveis inconsistências no formato, como linhas incompletas ou com quebras de linha dentro de campos.
<img width="643" height="256" alt="{43B8D467-39DE-47D1-8684-D550E6725EAB}" src="https://github.com/user-attachments/assets/556b44e8-f630-476b-9a59-d19c7cd658c1" />

## Transformações e Modelagem dos Dados
Após a criação das tabelas externas na camada *raw*, foram desenvolvidas consultas SQL no BigQuery com o objetivo de transformar, limpar e estruturar os dados para análise.
Essas consultas incluíram:
- Conversão de tipos de dados (como timestamps e ratings)
- Tratamento de valores inconsistentes ou ausentes  
- Padronização de colunas para facilitar a modelagem  
<img width="658" height="286" alt="{5EC83EEA-4B5D-40E0-8B7D-D7B6DE08AB2C}" src="https://github.com/user-attachments/assets/1293b674-a2d2-4cd9-b213-a9a88a750d81" />


### Modelagem Analítica (Fato e Dimensão)
A partir dos dados tratados, foi aplicada uma modelagem analítica baseada em tabelas fato e dimensão.
- **Tabelas dimensão** foram utilizadas para armazenar informações descritivas, como dados de filmes (título, gênero)  
- **Tabelas fato** concentraram eventos transacionais, como avaliações realizadas pelos usuários ao longo do tempo  
Essa estrutura permitiu maior eficiência nas consultas e melhor organização para consumo no dashboard.

### Criação de Views Analíticas
Foram criadas *views* no BigQuery para facilitar a análise e servir como base para o dashboard no Metabase. Essas views realizam agregações e cálculos importantes, como:
- Total de avaliações por período (ano e mês)  
- Distribuição de ratings por gênero  
- Relação entre popularidade (volume de avaliações) e qualidade (nota média)  
Essas abstrações simplificam o acesso aos dados e evitam a repetição de lógica nas visualizações.
<img width="672" height="198" alt="{697AA40B-6D44-49F3-98D1-0938EE7E890B}" src="https://github.com/user-attachments/assets/ad2d7542-68c2-4280-a4c4-0ddc75fe2403" />


### Suporte às Visualizações
As consultas SQL foram desenvolvidas com foco em atender diretamente às necessidades do dashboard, garantindo que os dados já estivessem agregados e prontos para visualização.
Isso possibilitou a construção de gráficos como:
- Heatmaps temporais  
- Rankings de gêneros  
- Análises comparativas entre filmes  
- Comportamento de usuários  

## Ferramentas Utilizadas
- **BigQuery**: para o armazenamento, processamento e consultas em larga escala.
- **Google Cloud Storage**: para armazenar os arquivos CSV brutos, que alimentam as tabelas externas.
- **Docker**: para criar um ambiente portátil e replicável, facilitando o desenvolvimento e execução.
- **Metabase**: para a criação do dashboard interativo, permitindo visualizações dinâmicas e filtros por gênero, tempo e popularidade.

## Configuração do Dashboard
O dashboard foi desenvolvido no Metabase, utilizando as tabelas externas criadas no BigQuery. As consultas agregam os ratings por ano e mês, e os gráficos incluem heatmaps, rankings de gêneros mais populares e correlações entre avaliações e frequência de visualização. O ambiente foi containerizado com Docker, garantindo portabilidade e facilidade de replicação.

## Resultados e Insights
A análise revelou que determinados gêneros, como drama e comédia, possuem uma popularidade mais constante ao longo do tempo, enquanto outros, como documentários, têm picos mais irregulares. Além disso, observamos uma correlação positiva entre a avaliação média dos filmes e a frequência de visualizações. Essas descobertas servem como base para decisões de marketing ou sugestões personalizadas de conteúdo.

