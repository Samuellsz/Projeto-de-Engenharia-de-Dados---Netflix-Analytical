# Projeto-de-Engenharia-de-Dados-Netflix-Analytical

## Objetivo
Este projeto teve como objetivo analisar padrões de popularidade e avaliação de filmes na plataforma Netflix. Utilizando dados extraídos de arquivos CSV, buscamos identificar quais gêneros se destacam, como as avaliações variam ao longo do tempo e quais fatores influenciam a popularidade dos títulos.

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


## Ferramentas Utilizadas
- **BigQuery**: para o armazenamento, processamento e consultas em larga escala.
- **Google Cloud Storage**: para armazenar os arquivos CSV brutos, que alimentam as tabelas externas.
- **Docker**: para criar um ambiente portátil e replicável, facilitando o desenvolvimento e execução.
- **Metabase**: para a criação do dashboard interativo, permitindo visualizações dinâmicas e filtros por gênero, tempo e popularidade.

## Configuração do Dashboard
O dashboard foi desenvolvido no Metabase, utilizando as tabelas externas criadas no BigQuery. As consultas agregam os ratings por ano e mês, e os gráficos incluem heatmaps, rankings de gêneros mais populares e correlações entre avaliações e frequência de visualização. O ambiente foi containerizado com Docker, garantindo portabilidade e facilidade de replicação.

## Resultados e Insights
A análise revelou que determinados gêneros, como drama e comédia, possuem uma popularidade mais constante ao longo do tempo, enquanto outros, como documentários, têm picos mais irregulares. Além disso, observamos uma correlação positiva entre a avaliação média dos filmes e a frequência de visualizações. Essas descobertas servem como base para decisões de marketing ou sugestões personalizadas de conteúdo.

