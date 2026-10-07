# Guia de Contribuição

## Fluxo de trabalho (GitHub Flow)

1. Crie uma **Issue** para a tarefa (ou use uma já existente).
2. Crie uma branch a partir da `main`: `feature/<numero-da-issue>-descricao-curta`
3. Faça commits pequenos e frequentes.
4. Abra um **Pull Request** vinculando a Issue (`Closes #número`).
5. Após revisão, faça o merge na `main` e apague a branch.

## Nomes de branches

| Prefixo | Uso |
|---------|-----|
| `feature/` | Nova funcionalidade ou documento |
| `fix/` | Correção |
| `docs/` | Documentação |
| `test/` | Testes |

## Padrão de commits (Conventional Commits)

```
<tipo>: <descrição curta no imperativo>
```

| Tipo | Quando usar |
|------|-------------|
| `feat` | Nova funcionalidade |
| `fix` | Correção de erro |
| `docs` | Documentação |
| `test` | Testes |
| `chore` | Tarefas de manutenção |
| `ci` | Configuração de CI/CD |

Exemplos:
- `docs: adiciona diagrama de classes`
- `feat: implementa cadastro de usuário`
- `test: adiciona casos de teste de login`

## Definition of Done
Veja [Metodologia Ágil](docs/04-metodologia-agil.md#6-definition-of-done-dod).
