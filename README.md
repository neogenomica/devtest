


# Teste Dev 2025

Por que trabalhar na NeoGenomica ?
===============================

A NeoGenomica entra no mercado como um dos principais laboratórios do Brasil a oferecer tecnologia de sequenciamento genético de nova geração, focada na identificação, análise e diagnóstico de doenças raras. Além disso, disponibilizamos uma ampla gama de exames genéticos voltados para análises clínicas.

Nossa equipe é composta por especialistas renomados em suas áreas, como biomédicos, médicos e bioinformatas, que utilizam as mais avançadas tecnologias e equipamentos para realizar testes genéticos de ponta. Em especial, o time de bioinformática lida diariamente com ferramentas, plataformas e sistemas que manipulam grandes volumes de dados gerados a partir do sequenciamento de DNA e bancos de dados sobre doenças genéticas.

Com o desafio de processar esses grandes volumes de dados, desenvolvemos ferramentas de alto desempenho e especializadas, que apoiam nossos analistas na realização de diagnósticos clínicos precisos. Na NeoGenomica, trabalhamos com Big Data voltado para a saúde, o que reforça nosso compromisso com a inovação. Fazer parte do nosso time significa colaborar com profissionais de diversas formações, unidos pelo objetivo de oferecer a milhões de brasileiros acesso a informações detalhadas e profundas sobre sua saúde, auxiliando-os em suas escolhas de vida.



## Teste técnico para processo seletivo NeoGenomica 🧬

## Objetivo

Criar uma aplicação web Full Stack (front-end + back-end) para o gerenciamento de primers utilizados em exames de pesquisa de mutações por sequenciamento genético. Este sistema deve permitir cadastrar, buscar, exportar e importar primers de forma eficiente.

## Contexto

Na rotina laboratorial, utilizamos primers para amplificação de regiões específicas do genoma humano. Cada primer é definido por diversas informações como sequência, localização no genoma, transcrito alvo e exon. Este sistema tem como objetivo facilitar o gerenciamento destes primers.

---

## Requisitos Obrigatórios 🛠️

### Funcionalidades

1. **CRUD de primers**
   - Campos obrigatórios:
     - `id` (auto-incremento ou UUID)
     - `label`
     - `foward_sequence`
     - `reverse_sequence`
     - `foward_temperature`
     - `reverse_temperature`
     - `chr`
     - `transcrito`
     - `start`
     - `end`
     - `conditions`
     - `exon`
     - `genome_version`
     - `bed`
     - `size`

| Campo                 | Tipo de Dado       | Exemplo                                           | Observações                                               |
| --------------------- | ------------------ | ------------------------------------------------- | --------------------------------------------------------- |
| `id`                  | Inteiro ou UUID    | `70`                                              | Pode ser gerado automaticamente pelo banco de dados       |
| `label`               | Texto (único)      | `PORCN_15`                                        | **Obrigatoriamente único**                                |
| `foward_sequence`     | Texto (DNA)        | `GGGCAAAGGATGGGTTTTC`                             | Sequência da fita forward (A, T, G, C)                    |
| `reverse_sequence`    | Texto (DNA)        | `CAGTGGCACCCTGAGAGG`                              | Sequência da fita reverse (A, T, G, C)                    |
| `foward_temperature`  | Decimal            | `61.6`                                            | Temperatura de anelamento da fita forward                 |
| `reverse_temperature` | Decimal            | `60.4`                                            | Temperatura de anelamento da fita reverse                 |
| `chr`                 | Seleção (dropdown) | `1`, `2`, ..., `22`, `X`, `Y`, `MT`               | Deve ser selecionado de uma lista fixa de cromossomos     |
| `transcrito`          | Texto              | `NM_203475.3`                                     | Identificador RefSeq                                      |
| `start`               | Inteiro            | `48520301`                                        | Início da região genômica (posição)                       |
| `end`                 | Inteiro            | `48520530`                                        | Final da região genômica (posição)                        |
| `conditions`          | Texto              | `TD66-60`                                         | Condição de uso do primer (ex: temperatura, protocolo)    |
| `exon`                | Texto              | `15`                                              | Número ou identificador do éxon                           |
| `genome_version`      | Seleção            | `hg19` ou `hg38`                                  | Versão do genoma de referência (apenas essas duas opções) |
| `bed`                 | Texto              | `chrX 48520301 48520530 PORCN_NM_203475.3_exon15` | Linha usada na exportação BED (separada por tab)          |
| `size`                | Texto              | `230pb`                                           | Tamanho do amplicon (ex: `230pb`)                         |



2. **Busca de primers**
   - Buscar por `label`, `foward_sequence` ou `reverse_sequence`.

3. **Exportação de BED**
   - Selecionar um ou mais primers e exportar em arquivo `.bed` com o seguinte formato:
     ```
     chrX    48520301    48520530    PORCN_NM_203475.3_exon15
     ```
   - O nome do arquivo deve ser definido pelo usuário no momento da exportação.
   - Separador deve ser tabulação (`\t`).

---

## Requisitos Bônus ⭐

1. **Filtro avançado**
   - Buscar primers por cromossomo (`chr`) e faixa de coordenadas (`start` a `end`).

2. **Importação via CSV**
   - Upload de um arquivo `.csv` contendo primers.
   - Se já existir um `label`, o registro deve ser sobrescrito.

3. **Autenticação**
   - Login para acessar o sistema.
   - Cada ação (cadastrar, editar, excluir, exportar) deve exigir autenticação.

---

## Requisitos Técnicos 🔧

- Você pode utilizar o stack que preferir, mas sugerimos:
  - **Front-end:** React, Vue.js ou Angular
  - **Back-end:** Ruby on Rails
  - **Banco de dados:** PostgreSQL ou outro relacional
- A aplicação pode rodar localmente, com instruções claras no `README` de como executar.

---

## Entrega

1. Faça um fork deste repositório.
2. Desenvolva sua solução em um branch chamado `develop`.
3. Envie o link do seu repositório com instruções de execução no `README`.

---

## Segundo Desafio - Discussão Técnica 🔐

### Tema: Estratégias de Autenticação e Segurança para Aplicações Web

Preparamos uma segunda parte do desafio que será discutida em uma chamada com os entrevistadores.

**Objetivo:** Apresente uma avaliação crítica sobre soluções de autenticação e segurança para a aplicação desenvolvida.

**Duração:**  
- Apresentação: até 15 minutos  
- Perguntas e respostas: 5 minutos

**Sugestões de tópicos para abordar:**

- Estratégias de autenticação (JWT, OAuth2, sessões, etc)
- Armazenamento seguro de senhas (bcrypt, scrypt)
- Controle de acesso (RBAC)
- Proteção contra ataques comuns (CSRF, XSS, SQL Injection)
- Uso de HTTPS, CORS e rate limiting
- Boas práticas com cookies e tokens

Você pode usar slides ou diagramas, se desejar.

---

## Critérios de Avaliação ✅

- Clareza e organização do código
- Boas práticas de desenvolvimento
- Cobertura dos requisitos obrigatórios e bônus
- Facilidade de uso da interface
- Segurança e robustez da autenticação
- Capacidade de argumentação técnica na discussão

---

## Exemplo de Entrada CSV (Cabeçalho obrigatório)

```csv
label,foward_sequence,reverse_sequence,foward_temperature,reverse_temperature,chr,transcrito,start,end,conditions,exon,genome_version,bed,size
PORCN_15,GGGCAAAGGATGGGTTTTC,CAGTGGCACCCTGAGAGG,61.6,60.4,X,NM_203475.3,48520301,48520530,TD66-60,15,hg38,chrX 48520301 48520530 PORCN_NM_203475.3_exon15,230pb
```

## Referências

- Adicionamos um exemplo de bed para download
- Adicionamos um exemplo de arquivo de teste de primers para importação manual ou via csv (upload)


- Para facilitar ao terminar o seu teste, commit todo o seu projeto no seu respositório forkeado (bifurcado) e nos envie o link do seu repositório junto a resposta do seu teste admissional.
