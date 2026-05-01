# Projeto-de-Engenharia-de-Dados-Netflix-Analytical

## Objetivo
Este projeto teve como objetivo analisar padrões de popularidade e avaliação de filmes disponíveis na plataforma Netflix. Utilizando dados extraídos de arquivos CSV, buscamos identificar quais gêneros se destacam, como as avaliações variam ao longo do tempo e quais fatores influenciam a popularidade dos títulos.

## Metodologia
Os dados foram obtidos a partir de arquivos CSV contendo informações detalhadas sobre filmes, como títulos, gêneros e notas. Após o download, carregamos esses dados no Google Cloud, utilizando o BigQuery para armazenar e processar as informações. Criamos tabelas dinâmicas, com dimensões e tabelas fato, para facilitar as análises. A partir dessas consultas, containerizamos a aplicação com Docker, permitindo a execução portátil do ambiente. Por fim, usamos o Metabase para a visualização interativa, desenvolvendo o dashboard final.

## Resultados e Insights
A análise revelou que determinados gêneros, como drama e comédia, possuem uma popularidade mais constante ao longo do tempo, enquanto outros, como documentários, têm picos mais irregulares. Além disso, observamos uma correlação positiva entre a avaliação média dos filmes e a frequência de visualizações. Essas descobertas servem como base para decisões de marketing ou sugestões personalizadas de conteúdo.

