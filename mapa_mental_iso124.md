# Mapa Mental: Ciclo de Vida e Engenharia de Software Avançada (ISO124)

Este documento contém a representação visual dos conceitos da disciplina de Desenvolvimento de Software II (ISO124), estruturada em um Mapa Mental e um Diagrama de Fluxo das Conexões Diretas ("Efeito Dominó").

---

## 🗺️ Mapa Mental (Estrutura e Conteúdo)

O mapa mental abaixo organiza as semanas e ramificações propostas a partir do núcleo central do Ciclo de Vida de Software (SDLC) e dos 4P's.

```mermaid
mindmap
  root(("SDLC & 4P's
    Pessoas | Processo | Produto | Planejamento"))
    ::icon(fa fa-project-diagram)
    R1["Ramificação 1: Concepção e Gestão do Escopo"]
      S1["Semana 1: Fundamentos e Metodologia"]
        S1_1[Metodologia Ágil / Scrum]
        S1_2[Formação de Times]
        S1_3["Ex: Decidir usar Scrum"]
      S2["Semana 2: Engenharia de Requisitos"]
        S2_1[Casos de Uso]
        S2_2[Requisitos de Integração]
        S2_3[Roadmap de alto nível]
        S2_4["Ex: Criar Caso de Uso 'Transferir Dinheiro'"]
      S3["Semana 3: Processamento do Backlog"]
        S3_1[Product Backlog]
        S3_2[Critérios INVEST]
        S3_3["Definição de Pronto (DoD)"]
        S3_4[Metas SMART]
        S3_5["Ex: User Story de Saldo (INVEST)"]
    R2["Ramificação 2: Engenharia de Código e Arquitetura"]
      S4["Semana 4: SCM Avançado e Boas Práticas"]
        S4_1[Git Branching]
        S4_2[Merge vs Rebase]
        S4_3["Princípios DRY, KISS e SoC"]
        S4_4["Ex: SoC na separação de cálculo de juros"]
      S6["Semana 6: Projeto de Sistemas e Arquitetura"]
        S6_1[Padrões Arquiteturais]
        S6_2[Modelo de Visão 4+1]
        S6_3[Modelo C4]
        S6_4["Ex: Diagrama C4 para Frontend/Backend"]
    R3["Ramificação 3: Qualidade, Governança e Alinhamento"]
      S5["Semana 5: Documentação Centrada na Wiki"]
        S5_1[Wiki Viva]
        S5_2[Markdown Especial]
        S5_3[Notas de Reunião]
        S5_4["Ex: Guia de branches na Wiki"]
    R4["Ramificação 4: Automação e Garantia de Qualidade"]
      S7["Semana 7: Testes de Desenvolvimento"]
        S7_1[Testes Unitários & Mocks]
        S7_2[TDD]
        S7_3[Cobertura de Código]
        S7_4["Ex: Teste unitário com Mock para 'Sacar Dinheiro'"]
      S8["Semana 8: Pipeline de CI/CD"]
        S8_1[Integração Contínua]
        S8_2[Automação de compilação]
        S8_3[Testes estáticos]
        S8_4[Regras de Merge Request]
        S8_5["Ex: Travar merge se cobertura < 80%"]
    R5["Ramificação 5: Entrega e Lançamento"]
      S9["Semana 9: Apresentação e Lançamento"]
        S9_1["Controle de Versão Semântico (SemVer)"]
        S9_2[Ciclo de Vida de Lançamento]
        S9_3["Demonstração do Produto (Review)"]
        S9_4["Ex: Publicar v1.0.0 do Sistema Bancário"]
```

---

## 🔗 O Efeito Dominó (Conexões e Dependências)

Como o mindmap representa uma árvore hierárquica pura, o fluxo abaixo demonstra o **Efeito Dominó** e a dependência direta entre as entregas de cada semana:

```mermaid
flowchart TD
    %% Estilos e Definições de Nós
    classDef scope fill:#d4edda,stroke:#28a745,stroke-width:2px,color:#155724;
    classDef arch fill:#cce5ff,stroke:#004085,stroke-width:2px,color:#004085;
    classDef gov fill:#fff3cd,stroke:#856404,stroke-width:2px,color:#856404;
    classDef qa fill:#f8d7da,stroke:#721c24,stroke-width:2px,color:#721c24;
    classDef release fill:#e2e3e5,stroke:#383d41,stroke-width:2px,color:#383d41;

    subgraph Escopo["Gestão de Escopo"]
        S1["Semana 1: Scrum & Times"]
        S2["Semana 2: Casos de Uso & Requisitos"]
        S3["Semana 3: Backlog (INVEST & SMART)"]
    end

    subgraph Arquitetura["Código & Arquitetura"]
        S4["Semana 4: Git Branching & SoC"]
        S6["Semana 6: Padrões & Diagrama C4"]
    end

    subgraph Governanca["Governança"]
        S5["Semana 5: Wiki & Guias"]
    end

    subgraph QA["Qualidade & Automação"]
        S7["Semana 7: Testes Unitários & Mocks"]
        S8["Semana 8: Pipeline de CI/CD"]
    end

    subgraph Entrega["Entrega"]
        S9["Semana 9: SemVer & Release v1.0.0"]
    end

    %% Relacionamentos do Fluxo
    S1 -->|Define processo de trabalho para| S2
    S2 -->|Gera requisitos para| S3
    S3 -->|Define Sprints que geram branches no| S4
    S4 -->|Código estruturado alimenta/respeita| S6
    
    S6 & S4 -->|Documentados de forma centralizada na| S5
    
    S4 -->|Base de código para| S7
    S6 -->|Lógica isolada facilita Mocks nos| S7
    S7 -->|Testes executados no| S8
    
    S8 -->|Garante estabilidade para gerar| S9

    %% Aplicação de Estilos
    class S1,S2,S3 scope;
    class S4,S6 arch;
    class S5 gov;
    class S7,S8 qa;
    class S9 release;
```
