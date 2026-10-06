# Documento de Requisitos

## 1. Atores

| Ator | Descrição |
|------|-----------|
| Jogador | Usuário final que otimiza a conexão |
| Administrador | Gerencia jogos, nós de rota e relatórios |
| Gateway de pagamento | Sistema externo que processa cobranças |

## 2. Requisitos Funcionais (RF)

| ID | Requisito | Prioridade |
|----|-----------|-----------|
| RF01 | O sistema deve permitir o cadastro de jogadores (nome, e-mail, senha). | Alta |
| RF02 | O sistema deve permitir login e logout com autenticação segura. | Alta |
| RF03 | O sistema deve permitir a recuperação de senha por e-mail. | Média |
| RF04 | O sistema deve listar o catálogo de jogos suportados. | Alta |
| RF05 | O jogador deve poder selecionar um jogo e a região do servidor. | Alta |
| RF06 | O sistema deve medir a latência até os nós de rota disponíveis. | Alta |
| RF07 | O sistema deve escolher automaticamente a rota de menor latência. | Alta |
| RF08 | O jogador deve poder ativar e desativar a otimização. | Alta |
| RF09 | O sistema deve exibir ping, jitter e perda de pacotes em tempo real. | Alta |
| RF10 | O sistema deve armazenar e exibir o histórico de sessões. | Média |
| RF11 | O jogador deve poder assinar um plano e pagar online. | Média |
| RF12 | O administrador deve poder cadastrar, editar e remover jogos. | Alta |
| RF13 | O administrador deve poder gerenciar nós de rota (ativar/desativar). | Média |
| RF14 | O administrador deve poder visualizar relatórios de uso. | Baixa |

## 3. Requisitos Não Funcionais (RNF)

| ID | Categoria | Requisito |
|----|-----------|-----------|
| RNF01 | Desempenho | A latência adicional introduzida pelo sistema deve ser de no máximo 10 ms em média. |
| RNF02 | Desempenho | A escolha da melhor rota deve ocorrer em até 5 segundos após ativar a otimização. |
| RNF03 | Disponibilidade | O serviço deve ter disponibilidade mínima de 99,5% ao mês. |
| RNF04 | Segurança | Todo tráfego entre cliente e API deve usar TLS 1.2 ou superior. |
| RNF05 | Segurança | Senhas devem ser armazenadas com hash (bcrypt) e nunca em texto puro. |
| RNF06 | Conformidade | O tratamento de dados pessoais deve seguir a LGPD. |
| RNF07 | Usabilidade | O jogador deve conseguir iniciar uma otimização em até 3 cliques. |
| RNF08 | Compatibilidade | O cliente deve funcionar em Windows 10 e 11. |
| RNF09 | Escalabilidade | A arquitetura deve suportar 10.000 usuários simultâneos. |
| RNF10 | Manutenibilidade | O código deve ter cobertura mínima de 70% em testes unitários. |

## 4. Regras de Negócio (RN)

| ID | Regra |
|----|-------|
| RN01 | O plano **Gratuito** permite otimizar 1 jogo por vez, com limite de 2 horas por dia. |
| RN02 | O plano **Premium** permite jogos ilimitados e sem limite de horas. |
| RN03 | Uma assinatura é cancelada automaticamente após 3 falhas consecutivas de pagamento. |
| RN04 | Um nó de rota inativo não pode ser escolhido na seleção automática. |
| RN05 | O e-mail do jogador deve ser único no sistema. |
| RN06 | Uma sessão de otimização só pode estar ativa para um jogo por vez por usuário. |

## 5. Rastreabilidade

| Requisito | User Story | Caso de Teste |
|-----------|-----------|----------------|
| RF01 | US01 | CT01, CT02 |
| RF02 | US02 | CT03, CT04 |
| RF04, RF05 | US03 | CT05 |
| RF06, RF07, RF08 | US04 | CT06, CT07 |
| RF09 | US05 | CT08 |
| RF10 | US06 | CT09 |
| RF11 | US07 | CT10 |
| RF12 | US08 | CT11 |
| RF13 | US09 | CT12 |
