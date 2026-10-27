# Agente Copilot do Hyperframes

## O que o agente faz

Executa tarefas de engenharia neste monorepo (CLI, core, engine/producer, player, studio, registry, skills, docs) seguindo `.github/copilot-instructions.md` e o perfil `.github/agents/hyperframes-agent.agent.md`. Sempre trabalha em branch própria e abre PR.

## Como delegar

1. Crie uma issue com o template **Tarefa para o agente** (`.github/ISSUE_TEMPLATE/agent-task.yml`) e atribua ao Copilot.
2. Em um PR existente, comente `@copilot` com a mudança pedida.

## Boas tarefas

- Corrigir um bug com teste de regressão em um pacote (ex.: parser no `packages/core`).
- Adicionar uma flag documentada a um comando do CLI, com atualização de `docs/packages/cli.mdx`.
- Criar/ajustar um bloco do `registry/` e validar com `npx hyperframes lint` e `check`.

## Tarefas que NÃO devem ser delegadas

- Release, publish (npm, ClawHub, catálogo) ou deploy (Lambda, Cloud Run).
- Qualquer coisa que exija segredos, tokens ou contas externas (HeyGen, Gemini).
- Mudanças de segurança sensíveis ou refactors amplos sem critério de aceite claro.

## Limites conhecidos

- Firewall do agente pode bloquear domínios; downloads em runtime podem falhar.
- Sem segredos: integrações opcionais (`GEMINI_API_KEY`, render em nuvem) não são testáveis.
- `ffmpeg` pode estar ausente: testes de mídia (ex.: `mediaGradeAnalyzer.test.ts`) falham por ambiente. TODO(confirmar): adicionar ffmpeg ao `copilot-setup-steps.yml`.
- Testes de render/regressão completos são pesados e podem não rodar no ambiente do agente.
