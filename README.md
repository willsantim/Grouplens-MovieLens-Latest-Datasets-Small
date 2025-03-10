# Grouplens-MovieLens-Latest-Datasets-Small

CEFSA - Centro Educacional da Fundação Salvador Arena
FESA - Faculdade Engenheiro Salvador Arena
William Santim - RA: 082220033 - Engenharia de Computação - EC6
Eletiva II - Ambientes Inteligentes
Atividade N1 - 1° Bimestre

### 1) DESCRIÇÃO DA BASE DE DADOS

### a) Descrição do DataSet
Este conjunto de dados (ml-latest-small) descreve a classificação de 5 estrelas e a atividade de marcação de texto livre do [MovieLens](http://movielens.org), um serviço de recomendação de filmes. 
Ele contém 100.836 classificações e 3.683 aplicações de marcação em 9.742 filmes. 
Esses dados foram criados por 610 usuários entre 29 de março de 1996 e 24 de setembro de 2018. Este conjunto de dados foi gerado em 26 de setembro de 2018.
Os dados estão contidos nos arquivos `links.csv`, `movies.csv`, `ratings.csv` e `tags.csv`. Mais detalhes sobre o conteúdo e o uso de todos esses arquivos a seguir.

### b) Significado de cada linha de arquivo E c) quais são os atributos (colunas) e seus tipos

***LINKS***
O dataset `links.csv` contém informações sobre filmes, incluindo identificadores que referenciam duas das principais bases de dados de filmes online: IMDb e TMDb. 

| Nome da Coluna | Descrição da Coluna                           | Tipo de Dado | Exemplo   |
|----------------|-----------------------------------------------|--------------|-----------|
| movieId        | Id único para cada filme                      | Integer      | 5         |
| imdbId         | Id único do filme na base de dados IMDb       | Integer      | 113041    |
| tmdbId         | Id único do filme na base de dados TMDb       | Integer      | 11862     |


***MOVIES***
O dataset `movies.csv` contém informações detalhadas sobre filmes, cada um identificado por um ID único, título gênero do filme.

| Nome da Coluna | Descrição da Coluna                   | Tipo de Dado | Exemplo                    |
|----------------|---------------------------------------|--------------|----------------------------|
| movieId        | Id único para cada filme              | Integer      | 2                          |
| title          | Título do filme (ano de lançamento)   | String       | Jumanji (1995)             |
| genres         | Gêneros do filme, separados por "|"   | String       | Adventure|Children|Fantasy |

***RATINGS***
O dataset `ratings.csv` armazena dados das avaliações realizadas por usuários, para diversos filmes. A informação do momento da avaliação também está disponível

| Nome da Coluna | Descrição da Coluna                        | Tipo de Dado | Exemplo     |
|----------------|--------------------------------------------|--------------|-------------|
| userId         | Id único para cada usuário                 | Integer      | 1           |
| movieId        | Id único do filme                          | Integer      | 3           |
| rating         | Avaliação atribuída ao filme               | Float        | 4.0         |
| timestamp      | Momento da avaliação                       | Integer      | 964981247   |

***TAGS***
O dataset `tags.csv` fornece informações sobre as tags associadas a filmes, por diferentes usuários. Cada registro inclui o id do usuário, id do filme, a tag atribuída e o momento em que a tag foi atribuída.

| Nome da Coluna | Descrição da Coluna                 | Tipo de Dado | Exemplo              |
|----------------|-------------------------------------|--------------|----------------------|
| userId         | Id único para cada usuário          | Integer      | 2                    |
| movieId        | Id único do filme associado à tag   | Integer      | 89774                |
| tag            | Tag atribuída ao filme pelo usuário | String       | MMA                  |
| timestamp      | Momento que a tag foi atribuída     | Integer      | 1445715200           |

### 2)PREPARAÇÃO DA BASE DE DADOS

### a)Identificou algum problema no dataset?

***LINKS***
- Nomes em inglês para as colunas, dificultando entendimento;
- Analisando os tipos de dados, tivemos o cenário mostrado abaixo. Para a Coluna ID Tmdb, o tipo de dado como "float64" está incorreto
  
| #   | Column    | Non-Null Count  | Dtype  
|---  |------     |--------------   |-----  
| 0   |movieId    |9742 non-null    |int64  
| 1   |imdbId     |9742 non-null    |int64  
| 2   |tmdbId     |9734 non-null    |float64

***MOVIES***

- Nomes em inglês para as colunas, dificultando entendimento;
- Analisando os dados da coluna "genres", não há separação entre os gêneros com espaço, apenas com o caractere "|". A Ausência de espaço faz com que os elementos possam parecer mais grudados, dificultando a visualização.
  
| #   | Column    | Non-Null Count  | Dtype  
|---  |------     |--------------   |-----  
| 0   |movieId    |9742 non-null    |int64  
| 1   |title      |9742 non-null    |object 
| 2   |genres     |9734 non-null    |object

***RATINGS***

- Nomes em inglês para as colunas, dificultando entendimento;
- Analisando os tipos de dados, tivemos o cenário mostrado abaixo. Para a Coluna timestamp, o tipo de dado como "int64" está incorreto, pois não é facilmente legível ou interpretável sem conversão, além de que Debugging e logs ficam mais difíceis de analisar sem ferramentas específicas.

| #   | Column    | Non-Null Count  | Dtype  
|---  |------     |--------------   |-----  
| 0   |userId     |100836 non-null  |int64  
| 1   |movieId    |100836 non-null  |int64 
| 2   |rating     |100836 non-null  |float64
| 3   |timestamp  |100836 non-null  |int64

***TAGS***

- Nomes em inglês para as colunas, dificultando entendimento;
- Analisando os tipos de dados, tivemos o cenário mostrado abaixo. Para a Coluna timestamp, o tipo de dado como "int64" está incorreto, pois não é facilmente legível ou interpretável sem conversão, além de que Debugging e logs ficam mais difíceis de analisar sem ferramentas específicas.

| #   | Column    | Non-Null Count  | Dtype  
|---  |------     |--------------   |-----  
| 0   |userId     |100836 non-null  |int64  
| 1   |movieId    |100836 non-null  |int64 
| 2   |tag        |100836 non-null  |object
| 3   |timestamp  |100836 non-null  |int64

### b)Aplicou alguma correção para os problemas identificados no item anterior?

***LINKS***
- Nomes das colunas alterados para português;
- Alteração do tipo de dado da Coluna ID Tmdb, de "float64" para "int64".
  
| #   | Column    | Non-Null Count  | Dtype  
|---  |------     |--------------   |-----  
| 0   |ID Filme   |9742 non-null    |int64  
| 1   |ID Imdb    |9742 non-null    |int64  
| 2   |ID Tmdb    |9742 non-null    |int64

***MOVIES***

- Nomes das colunas alterados para português;
- Alteração dos dados da coluna "genres", separação que era feita pelo caractere "|", mudou para " | ".
  
| #   | Column    | Non-Null Count  | Dtype  
|---  |------     |--------------   |-----  
| 0   |ID Filme   |9742 non-null    |int64  
| 1   |Título	    |9742 non-null    |object 
| 2   |Genero     |9734 non-null    |object

***RATINGS***

- Nomes das colunas alterados para português;
- Alteração do tipo de dado na coluna "Data e Hora Avaliação", de "int64" para "datetime64[ns]".

| #   | Column                | Non-Null Count  | Dtype  
|---  |------                 |--------------   |-----  
| 0   |ID Usuario             |100836 non-null  |int64  
| 1   |ID Filme               |100836 non-null  |int64 
| 2   |Avaliação              |100836 non-null  |float64
| 3   |Data e Hora Avaliação  |100836 non-null  |datetime64[ns]

***TAGS***

- Nomes das colunas alterados para português;
- Alteração do tipo de dado na coluna "Data e Hora da Tag", de "int64" para "datetime64[ns]".

| #   | Column                | Non-Null Count  | Dtype  
|---  |------                 |--------------   |-----  
| 0   |ID Usuario             |100836 non-null  |int64  
| 1   |ID Filme               |100836 non-null  |int64 
| 2   |Tag                    |100836 non-null  |object64
| 3   |Data e Hora da Tag     |100836 non-null  |datetime64[ns]
