# Plano de Testes

## 1. Estratégia

| Nível | Objetivo | Ferramenta planejada |
|-------|----------|----------------------|
| Unitário | Testar funções e classes isoladas | Jest |
| Integração | Testar API + banco de dados | Jest + Supertest |
| Sistema (E2E) | Testar fluxos completos do usuário | Playwright |
| Desempenho | Validar RNF01, RNF02 e RNF09 | k6 |
| Segurança | Validar RNF04 e RNF05 | OWASP ZAP |

**Critério de aprovação:** 100% dos casos críticos aprovados e cobertura mínima de 70%.

## 2. Casos de Teste

| ID | Requisito | Descrição | Entrada | Resultado esperado | Tipo |
|----|-----------|-----------|---------|-------------------|------|
| CT01 | RF01 | Cadastro com dados válidos | Nome, e-mail novo, senha com 8+ caracteres | Conta criada | Funcional |
| CT02 | RF01 / RN05 | Cadastro com e-mail duplicado | E-mail já existente | Erro "e-mail já cadastrado" | Funcional |
| CT03 | RF02 | Login válido | E-mail e senha corretos | Acesso ao painel | Funcional |
| CT04 | RF02 | Login inválido | Senha incorreta | Mensagem de erro, sem acesso | Funcional |
| CT05 | RF04 / RF05 | Listar jogos e escolher região | Jogo ativo + região | Preferência salva | Funcional |
| CT06 | RF06 / RF07 | Escolha da melhor rota | 3 nós com latências 40, 25 e 60 ms | Nó de 25 ms escolhido | Funcional |
| CT07 | RN04 | Ignorar nó inativo | Nó mais rápido marcado como inativo | Nó inativo não é escolhido | Funcional |
| CT08 | RF09 | Atualização de métricas | Sessão ativa por 10 s | 10 atualizações exibidas | Funcional |
| CT09 | RF10 | Histórico de sessões | Usuário com 3 sessões | Lista com 3 registros | Funcional |
| CT10 | RF11 / RN03 | Falha de pagamento | Cartão recusado | Plano permanece inalterado | Funcional |
| CT11 | RF12 | Desativar jogo | Admin desativa um jogo | Jogo some do catálogo | Funcional |
| CT12 | RF13 | Desativar nó | Admin desativa um nó | Nó fora da seleção automática | Funcional |
| CT13 | RNF01 | Latência adicional | 1.000 medições | Média de até 10 ms | Desempenho |
| CT14 | RNF05 | Senha armazenada com hash | Inspeção do banco | Nenhuma senha em texto puro | Segurança |
| CT15 | RN01 | Limite do plano gratuito | 2h de uso no dia | Otimização bloqueada | Funcional |

## 3. Matriz de rastreabilidade
Veja a seção 5 de [Requisitos](01-requisitos.md).

## 4. Registro de execução (modelo)

| ID | Data | Responsável | Resultado | Observações |
|----|------|-------------|-----------|-------------|
| CT01 | | | ☐ Passou ☐ Falhou | |
