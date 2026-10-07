# Modelagem do Sistema

Os diagramas abaixo usam **Mermaid**, que o GitHub renderiza automaticamente.

## 1. Diagrama de Casos de Uso

```mermaid
flowchart LR
    J([Jogador])
    A([Administrador])
    G([Gateway de pagamento])

    subgraph PingFlow
        UC1(Cadastrar conta)
        UC2(Fazer login)
        UC3(Escolher jogo e região)
        UC4(Ativar otimização)
        UC5(Ver métricas em tempo real)
        UC6(Consultar histórico)
        UC7(Assinar plano)
        UC8(Gerenciar jogos)
        UC9(Gerenciar nós de rota)
        UC10(Ver relatórios)
    end

    J --- UC1
    J --- UC2
    J --- UC3
    J --- UC4
    J --- UC5
    J --- UC6
    J --- UC7
    UC7 --- G
    A --- UC2
    A --- UC8
    A --- UC9
    A --- UC10
    UC4 -. inclui .-> UC3
```

## 2. Diagrama de Classes

```mermaid
classDiagram
    class Usuario {
        +int id
        +string nome
        +string email
        +string senhaHash
        +login()
        +logout()
    }
    class Jogador {
        +string regiaoPreferida
        +iniciarSessao()
        +encerrarSessao()
    }
    class Administrador {
        +cadastrarJogo()
        +gerenciarNo()
        +gerarRelatorio()
    }
    class Plano {
        +int id
        +string nome
        +decimal preco
        +int limiteHorasDia
    }
    class Assinatura {
        +int id
        +date inicio
        +date fim
        +string status
    }
    class Pagamento {
        +int id
        +decimal valor
        +string status
        +date data
    }
    class Jogo {
        +int id
        +string nome
        +boolean ativo
    }
    class ServidorJogo {
        +int id
        +string regiao
        +string enderecoIP
    }
    class NoRota {
        +int id
        +string localizacao
        +boolean ativo
        +medirLatencia()
    }
    class SessaoOtimizacao {
        +int id
        +datetime inicio
        +datetime fim
        +float pingMedio
    }
    class Metrica {
        +datetime instante
        +float ping
        +float jitter
        +float perdaPacotes
    }

    Usuario <|-- Jogador
    Usuario <|-- Administrador
    Jogador "1" --> "0..*" Assinatura
    Assinatura "*" --> "1" Plano
    Assinatura "1" --> "0..*" Pagamento
    Jogador "1" --> "0..*" SessaoOtimizacao
    SessaoOtimizacao "*" --> "1" Jogo
    SessaoOtimizacao "*" --> "1" NoRota
    SessaoOtimizacao "1" --> "0..*" Metrica
    Jogo "1" --> "1..*" ServidorJogo
```

## 3. Diagrama de Sequência: Ativar otimização

```mermaid
sequenceDiagram
    actor J as Jogador
    participant C as Cliente (App)
    participant API as API PingFlow
    participant R as Serviço de Rotas
    participant N as Nós de Rota

    J->>C: Seleciona jogo e clica em "Otimizar"
    C->>API: POST /sessoes (jogoId, regiao)
    API->>API: Valida plano e limite de horas
    API->>R: Solicitar melhor rota
    R->>N: Medir latência (ping) de cada nó ativo
    N-->>R: Latências medidas
    R-->>API: Nó com menor latência
    API-->>C: Sessão criada + rota escolhida
    C-->>J: Exibe "Otimização ativa" e métricas
    loop A cada 1 segundo
        C->>API: Enviar métricas (ping, jitter, perda)
        API-->>C: Confirmação
    end
```

## 4. Diagrama de Atividades: Fluxo de otimização

```mermaid
flowchart TD
    A([Início]) --> B[Jogador faz login]
    B --> C[Escolhe jogo e região]
    C --> D{Plano permite?}
    D -- Não --> E[Exibir aviso de limite / oferecer Premium]
    E --> Z([Fim])
    D -- Sim --> F[Medir latência dos nós ativos]
    F --> G[Escolher nó com menor latência]
    G --> H[Ativar otimização]
    H --> I[Exibir métricas em tempo real]
    I --> J{Jogador encerra?}
    J -- Não --> I
    J -- Sim --> K[Salvar sessão no histórico]
    K --> Z
```

## 5. Modelo Entidade-Relacionamento (DER)

```mermaid
erDiagram
    USUARIO ||--o{ ASSINATURA : possui
    PLANO ||--o{ ASSINATURA : define
    ASSINATURA ||--o{ PAGAMENTO : gera
    USUARIO ||--o{ SESSAO : inicia
    JOGO ||--o{ SESSAO : e_otimizado_em
    JOGO ||--|{ SERVIDOR_JOGO : possui
    NO_ROTA ||--o{ SESSAO : roteia
    SESSAO ||--o{ METRICA : registra

    USUARIO {
        int id PK
        string nome
        string email UK
        string senha_hash
        string perfil
    }
    PLANO {
        int id PK
        string nome
        decimal preco
        int limite_horas_dia
    }
    ASSINATURA {
        int id PK
        int usuario_id FK
        int plano_id FK
        date inicio
        date fim
        string status
    }
    PAGAMENTO {
        int id PK
        int assinatura_id FK
        decimal valor
        string status
        datetime data
    }
    JOGO {
        int id PK
        string nome
        boolean ativo
    }
    SERVIDOR_JOGO {
        int id PK
        int jogo_id FK
        string regiao
        string endereco_ip
    }
    NO_ROTA {
        int id PK
        string localizacao
        boolean ativo
    }
    SESSAO {
        int id PK
        int usuario_id FK
        int jogo_id FK
        int no_rota_id FK
        datetime inicio
        datetime fim
        float ping_medio
    }
    METRICA {
        int id PK
        int sessao_id FK
        datetime instante
        float ping
        float jitter
        float perda_pacotes
    }
```
