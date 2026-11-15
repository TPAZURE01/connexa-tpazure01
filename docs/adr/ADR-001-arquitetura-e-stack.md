# ADR-001 — Arquitetura e Stack Tecnológica

- **Situação:** aceita
- **Data:** <2026-11-15>
- **Participantes:** tetetete3232, DavisJunior-art, viniciusdeoliveiraz9

## Contexto

Precisamos definir uma base técnica única para uma equipe de 4 a 5 alunos desenvolver o Projeto Connexa durante a disciplina de Engenharia de Software. Como o código será gerado por agentes de IA (Copilot/Codex) a partir de tarefas do Azure Boards e o tempo das sprints é curto, precisamos de um ambiente padronizado, fácil de rodar (localmente, no Codespaces e no CI) e com regras claras para evitar que o agente adicione bibliotecas desnecessárias ou quebre a estrutura do projeto.

## Decisão

Adotamos o template monolítico modular com back-end em **.NET** e front-end em **React**. 

## Alternativas consideradas

| Alternativa | Por que não foi escolhida |
|---|---|
| Criar o projeto do zero sem template | Consome tempo valioso da sprint na configuração inicial e aumenta o risco de erros de integração com o CI e o agente de IA. |
| Outras stacks (ex: Node.js/Python + Vue/Angular) | A equipe optou pelo modelo oficial .NET + React já preparado com testes arquiteturais e regras de validação prontas. |

## Consequências

- **Positivas:** Ambiente pronto e idêntico para todos os membros e para o CI; fronteiras entre módulos protegidas contra alterações indevidas do agente de IA; builds reprodutíveis.
- **Negativas:** Proibição de instalar novas bibliotecas livremente durante as sprints (qualquer mudança exige um novo ADR); necessidade de limpar as tabelas do banco antes de rodar cada teste.
- **Como verificar:** Execução dos testes automatizados (incluindo NetArchTest no back-end e lint/build no front-end) e aprovação obrigatória dos checks no Pull Request antes do merge.
