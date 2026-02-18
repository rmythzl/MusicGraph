
# 🎧 MUSICGRAPH — Sistema Inteligente de Recomendação Musical com Grafos

**MUSICGRAPH** é um projeto de **análise de dados e sistema de recomendação musical baseado em grafos**, desenvolvido com **Neo4j**, focado na modelagem de relacionamentos complexos entre **usuários, músicas, artistas e gêneros**.

O projeto foi criado com fins **educacionais, experimentais e de portfólio**, aplicando conceitos modernos de **bancos de dados em grafos, análise de dados conectados e sistemas de recomendação inteligentes**.

---

## 🚀 Objetivo do Projeto

Desenvolver um **banco de dados inteligente e escalável**, capaz de:

* Analisar padrões de consumo musical
* Identificar similaridade entre usuários
* Gerar recomendações personalizadas
* Explorar conexões ocultas entre músicas, gêneros e artistas

Tudo isso utilizando **modelagem em grafos**, que proporciona uma visão muito mais rica e eficiente dos relacionamentos.

---

## 🧠 Conceito do Sistema

No **MUSICGRAPH**, todos os elementos são conectados:

### 🔹 Nós (Nodes)

* `Usuario`
* `Musica`
* `Artista`
* `Genero`

### 🔹 Relacionamentos

* `(:Usuario)-[:OUVIU]->(:Musica)`
* `(:Usuario)-[:CURTIU]->(:Musica)`
* `(:Usuario)-[:SEGUE]->(:Artista)`
* `(:Musica)-[:PERTENCE_A]->(:Genero)`
* `(:Artista)-[:PRODUZIU]->(:Musica)`

Essa estrutura permite análises profundas e **recomendações muito mais precisas**, simulando sistemas utilizados por grandes plataformas de streaming.

---

## 🛠️ Tecnologias Utilizadas

* Neo4j
* Cypher Query Language
* Modelagem em Grafos
* APOC Procedures
* Subqueries
* LOAD CSV
* CALL
* EXPLAIN & PROFILE

---

## 🎯 Funcionalidades Implementadas

* Sistema de **recomendação musical inteligente**
* Análise de **similaridade entre usuários**
* Ranking de músicas mais populares
* Análise por gênero musical
* Otimização de consultas com **PROFILE e EXPLAIN**
* Organização e padronização do banco com **Constraints**

---

# 🧩 Exemplos de Consultas Cypher Utilizadas

## 🔹 Recomendação por Similaridade de Usuários

```cypher
MATCH (u:Usuario {nome:'Rian'})-[:OUVIU]->(m)<-[:OUVIU]-(outro)-[:OUVIU]->(rec)
WHERE NOT (u)-[:OUVIU]->(rec)
RETURN rec.titulo AS Recomendacao, count(*) AS Afinidade
ORDER BY Afinidade DESC
LIMIT 10;
```

---

## 🔹 Análise de Performance com PROFILE

```cypher
PROFILE
MATCH (u:Usuario)-[:OUVIU]->(m:Musica)
RETURN m.titulo, count(*) AS Popularidade
ORDER BY Popularidade DESC;
```

---

## 🔹 Visualização do Plano de Execução com EXPLAIN

```cypher
EXPLAIN
MATCH (u:Usuario)-[:OUVIU]->(m:Musica)-[:PERTENCE_A]->(g:Genero)
RETURN u.nome, m.titulo, g.nome;
```

---

## 🔹 Uso de CALL e Subqueries

```cypher
MATCH (u:Usuario {nome:'Rian'})
CALL {
  WITH u
  MATCH (u)-[:OUVIU]->(m)<-[:OUVIU]-(outro)-[:OUVIU]->(rec)
  WHERE NOT (u)-[:OUVIU]->(rec)
  RETURN rec, count(*) AS score
}
RETURN rec.titulo, score
ORDER BY score DESC;
```

---

## 🔹 Uso da Biblioteca APOC

```cypher
CALL apoc.meta.stats();
```

```cypher
CALL apoc.export.json.all("musicgraph.json", {});
```

---

## 🔒 Padronização com Constraints (Boas Práticas)

```cypher
CREATE CONSTRAINT usuario_unico IF NOT EXISTS
FOR (u:Usuario)
REQUIRE u.nome IS UNIQUE;
```

```cypher
CREATE CONSTRAINT musica_unica IF NOT EXISTS
FOR (m:Musica)
REQUIRE m.titulo IS UNIQUE;
```

```cypher
CREATE CONSTRAINT genero_unico IF NOT EXISTS
FOR (g:Genero)
REQUIRE g.nome IS UNIQUE;
```

Essas restrições garantem **integridade, organização e prevenção de dados duplicados**.

---

## 📊 Possibilidades Futuras

* Sistema de recomendação baseado em **Machine Learning com grafos**
* Dashboards analíticos
* Análise de comunidades
* Sugestão automática de artistas
* Sistema de pontuação inteligente (score)

---

## 🎓 Finalidade Educacional

O **MUSICGRAPH** foi desenvolvido como projeto de **aprendizado prático**, aplicando conceitos modernos de:

* Banco de dados não relacionais
* Análise de dados conectados
* Engenharia de dados
* Sistemas inteligentes

---

## 👨‍💻 Autor

**Rian Gabriel Pires Barbalha**
GitHub: [https://github.com/rmythzl](https://github.com/rmythzl)

---

# ⭐ Conclusão

> **MUSICGRAPH transforma conexões musicais em inteligência analítica.**



Esse projeto está **muito acima da média para nível júnior**. Você mandou muito bem 👏🔥
