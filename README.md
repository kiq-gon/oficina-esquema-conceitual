 Projeto: Esquema Conceitual - Oficina Mecânica

Este projeto faz parte de um desafio de modelagem conceitual de banco de dados. O objetivo é criar um **modelo conceitual** para um sistema de controle e gerenciamento de ordens de serviço em uma oficina mecânica.

---

## Narrativa do Desafio

> Sistema de controle e gerenciamento de execução de ordens de serviço em uma oficina mecânica.
>
> - Clientes levam veículos à oficina para conserto ou revisões periódicas.
> - Cada veículo é designado a uma equipe de mecânicos que identifica os serviços a serem executados e preenche uma OS (Ordem de Serviço) com data de entrega.
> - A partir da OS, calcula-se o valor de cada serviço, consultando-se uma tabela de mão-de-obra.
> - O valor de cada peça também compõe a OS.
> - O cliente autoriza a execução dos serviços.
> - A mesma equipe avalia e executa os serviços.
> - Mecânicos possuem código, nome, endereço e especialidade.
> - Cada OS possui: número, data de emissão, valor, status e data para conclusão dos trabalhos.

---

##  Objetivo

Desenvolver o esquema conceitual com entidades, atributos e relacionamentos, cobrindo os requisitos apresentados na narrativa.

---

## Modelo Conceitual

### Entidades e Atributos

- **Cliente**
  - id_cliente (PK)
  - nome
  - telefone
  - endereco

- **Veículo**
  - id_veiculo (PK)
  - placa
  - modelo
  - marca
  - ano
  - id_cliente (FK)

- **Mecânico**
  - id_mecanico (PK)
  - nome
  - endereco
  - especialidade

- **Equipe**
  - id_equipe (PK)
  - nome_da_equipe

- **Ordem_Servico**
  - id_os (PK)
  - data_emissao
  - valor_total
  - status
  - data_conclusao
  - id_veiculo (FK)
  - id_equipe (FK)

- **Serviço**
  - id_servico (PK)
  - descricao
  - valor_mao_de_obra

- **Peça**
  - id_peca (PK)
  - descricao
  - valor_unitario

---

### Relacionamentos

- Cliente 1:N Veículo
- Veículo 1:N Ordem_Servico
- Equipe 1:N Ordem_Servico
- Equipe N:M Mecânico (via tabela **Equipe_Mecanico**)
- Ordem_Servico N:M Serviço (via tabela **OS_Servico**)
- Ordem_Servico N:M Peça (via tabela **OS_Peca**)

---

### Tabelas de Associação

- **Equipe_Mecanico**
  - id_equipe (FK)
  - id_mecanico (FK)

- **OS_Servico**
  - id_os (FK)
  - id_servico (FK)
  - quantidade
  - valor_unitario

- **OS_Peca**
  - id_os (FK)
  - id_peca (FK)
  - quantidade
  - valor_unitario

---

## Observações

- A tabela **Equipe_Mecanico** resolve o relacionamento N:M entre Equipe e Mecânico.
- As tabelas **OS_Servico** e **OS_Peca** detalham os itens da OS com suas quantidades e valores unitários.
- O modelo foi elaborado para atender aos requisitos da narrativa. Em caso de pontos não especificados, foram feitas decisões de modelagem baseadas no contexto usual de sistemas de oficina.
