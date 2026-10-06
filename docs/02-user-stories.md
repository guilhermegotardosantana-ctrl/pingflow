# User Stories

Formato: **Como** [ator], **quero** [ação], **para** [benefício].

---

### US01 – Cadastro de conta
**Como** jogador, **quero** criar uma conta, **para** acessar o PingFlow.

**Critérios de aceite**
- [ ] Dado um e-mail novo e senha válida, quando eu enviar o formulário, então a conta é criada.
- [ ] Dado um e-mail já cadastrado, então o sistema exibe erro de e-mail duplicado.
- [ ] A senha deve ter no mínimo 8 caracteres.

### US02 – Login
**Como** jogador, **quero** entrar com e-mail e senha, **para** usar minha conta com segurança.

**Critérios de aceite**
- [ ] Credenciais corretas levam ao painel principal.
- [ ] Credenciais incorretas exibem mensagem genérica de erro.
- [ ] Após 5 tentativas falhas, a conta é bloqueada por 15 minutos.

### US03 – Escolher jogo e região
**Como** jogador, **quero** escolher um jogo e a região do servidor, **para** otimizar a conexão certa.

**Critérios de aceite**
- [ ] O catálogo lista apenas jogos ativos.
- [ ] É possível filtrar jogos por nome.
- [ ] A região escolhida fica salva como preferência.

### US04 – Otimização automática de rota
**Como** jogador, **quero** ativar a otimização com um clique, **para** reduzir meu ping sem configurar nada.

**Critérios de aceite**
- [ ] O sistema mede a latência de todos os nós ativos.
- [ ] A rota de menor latência é selecionada em até 5 segundos.
- [ ] O jogador pode desativar a otimização a qualquer momento.

### US05 – Painel de métricas
**Como** jogador, **quero** ver ping, jitter e perda de pacotes em tempo real, **para** saber se a otimização está funcionando.

**Critérios de aceite**
- [ ] As métricas atualizam a cada 1 segundo.
- [ ] O painel mostra o ping antes e depois da otimização.

### US06 – Histórico de sessões
**Como** jogador, **quero** consultar minhas sessões anteriores, **para** acompanhar a qualidade da minha conexão ao longo do tempo.

**Critérios de aceite**
- [ ] A lista mostra data, jogo, duração e ping médio.
- [ ] É possível filtrar por período.

### US07 – Assinatura Premium
**Como** jogador, **quero** assinar o plano Premium, **para** otimizar jogos ilimitados.

**Critérios de aceite**
- [ ] O pagamento é processado pelo gateway externo.
- [ ] Após a confirmação, os benefícios são liberados imediatamente.
- [ ] Falha no pagamento exibe mensagem clara e não altera o plano.

### US08 – Gerenciar jogos
**Como** administrador, **quero** cadastrar e editar jogos, **para** manter o catálogo atualizado.

**Critérios de aceite**
- [ ] Posso criar, editar e desativar um jogo.
- [ ] Jogo desativado deixa de aparecer para os jogadores.

### US09 – Gerenciar nós de rota
**Como** administrador, **quero** ativar ou desativar nós de rota, **para** manter apenas servidores saudáveis em uso.

**Critérios de aceite**
- [ ] Nó desativado não é escolhido na seleção automática.
- [ ] Alterações ficam registradas com data e responsável.
