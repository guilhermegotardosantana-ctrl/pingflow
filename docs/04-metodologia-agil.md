# Metodologia Ágil

O projeto adota **Scrum**, organizado com **Issues** e **Milestones** do GitHub.

## 1. Papéis

| Papel | Responsável |
|-------|-------------|
| Product Owner | Guilherme Gotardo Santana |
| Scrum Master | Guilherme Gotardo Santana |
| Time de desenvolvimento | Guilherme Gotardo Santana |

> Como o trabalho é individual, os três papéis são exercidos pela mesma pessoa.

## 2. Cerimônias

| Cerimônia | Frequência | Objetivo |
|-----------|-----------|----------|
| Sprint Planning | Início de cada sprint | Definir o que entra na sprint |
| Daily (registrada em Issue) | Diária | Registrar o que foi feito e os impedimentos |
| Sprint Review | Fim da sprint | Validar as entregas |
| Retrospectiva | Fim da sprint | Melhorar o processo |

## 3. Product Backlog

| Prioridade | Item | Requisitos | Estimativa (pontos) |
|-----------|------|-----------|---------------------|
| 1 | US01 Cadastro de conta | RF01 | 3 |
| 2 | US02 Login | RF02 | 3 |
| 3 | US03 Escolher jogo e região | RF04, RF05 | 5 |
| 4 | US08 Gerenciar jogos | RF12 | 5 |
| 5 | US04 Otimização automática | RF06, RF07, RF08 | 8 |
| 6 | US05 Painel de métricas | RF09 | 5 |
| 7 | US06 Histórico de sessões | RF10 | 3 |
| 8 | US07 Assinatura Premium | RF11 | 8 |
| 9 | US09 Gerenciar nós de rota | RF13 | 3 |
| 10 | Relatórios de uso | RF14 | 5 |
| 11 | Recuperação de senha | RF03 | 2 |

## 4. Sprints

### Sprint 1 (2 semanas): Base do sistema
**Meta:** permitir que o jogador crie conta, entre e escolha um jogo.

| Item | Pontos | Status |
|------|--------|--------|
| US01 Cadastro de conta | 3 | Concluído |
| US02 Login | 3 | Concluído |
| US03 Escolher jogo e região | 5 | Concluído |
| US08 Gerenciar jogos | 5 | Concluído |

**Velocidade:** 16 pontos

### Sprint 2 (2 semanas): Otimização
**Meta:** entregar o núcleo do produto, a otimização de rota com métricas.

| Item | Pontos | Status |
|------|--------|--------|
| US04 Otimização automática | 8 | Concluído |
| US05 Painel de métricas | 5 | Concluído |
| US06 Histórico de sessões | 3 | Em andamento |

**Velocidade:** 13 pontos (histórico segue para a próxima sprint)

### Retrospectiva da Sprint 2
- **O que foi bem:** definição clara dos critérios de aceite.
- **O que melhorar:** estimar melhor as tarefas de integração entre módulos.
- **Ação:** quebrar histórias maiores que 5 pontos em tarefas menores.

## 5. Definition of Ready (DoR)
- História escrita no formato padrão
- Critérios de aceite definidos
- Estimada em pontos

## 6. Definition of Done (DoD)
- Critérios de aceite atendidos
- Testes escritos e passando
- Documentação atualizada
- Pull Request revisado e mesclado na `main`

## 7. Organização no GitHub

| Elemento Scrum | Recurso do GitHub |
|----------------|-------------------|
| Product Backlog | Issues abertas, sem Milestone |
| Sprint | Milestone |
| História / tarefa | Issue |
| Entrega | Pull Request |
