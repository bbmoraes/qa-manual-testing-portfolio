# QA Manual Testing Portfolio 🧪

Estudo prático de testes funcionais pela interface do **SauceDemo**, com plano, casos executados, falhas reproduzidas e evidências reais.

**Portfólio de Bianca Moraes · [@bbmoraes](https://github.com/bbmoraes)**  
Execução EX-001: **21/10/2026**, America/Sao_Paulo. Projeto educacional com assistência de IA operando o navegador e organizando a documentação; a execução independente pela estudante ainda não foi avaliada.

## Resultados verificáveis

| Casos registrados | Executados | Passed | Failed | Blocked | Not Run | Falhas reproduzidas |
|---:|---:|---:|---:|---:|---:|---:|
| 27 | 25 | 22 | 3 | 0 | 2 | 3 |

Aprovação: **88% dos 25 executados**. Repetições de uma falha não inflaram a contagem. Os dois Not Run correspondem a pesquisa e edição de quantidade, cujos controles não foram encontrados no fluxo examinado. A contagem não representa cobertura total do produto. Fonte: [casos e resultados](test-cases/test-cases.md), [dados estruturados](test-execution/results.json) e [métricas](test-execution/metrics.json).

## Objetivo e aplicação

Demonstrar planejamento, raciocínio de teste, comparação esperado/obtido, reprodução de defeitos e comunicação técnica para uma posição inicial de QA.

Aplicação: [SauceDemo](https://www.saucedemo.com/), uma aplicação de demonstração da Sauce Labs ([repositório oficial](https://github.com/saucelabs/sample-app-web)). A própria tela publica contas de teste. O fluxo permite testar login, catálogo e pedido fictício sem informar pagamento real. Não foram usados dados da Magenta ou de clientes.

## Escopo e técnicas

- Login positivo e negativo, campos obrigatórios e conta bloqueada.
- Ordenação de preços e nomes, detalhes, inclusão/remoção e persistência do carrinho por recarga.
- Validação de formulário, soma de totais, cancelamento e conclusão fictícia de compra.
- Caixa-preta, partição de equivalência, exploração guiada por risco, transições de estado e limites observáveis de cardinalidade e campos vazios. Comprimentos máximos e regras postais não foram especificados nem validados.
- Comparação entre standard_user e problem_user; dois ensaios por falha na mesma sessão.

Ferramentas: **Chrome**, controle assistido do navegador, capturas JPEG e leitura do DOM visível; Markdown/JSON para documentação e Python para organização, contagens e integridade do pacote. As interações foram dirigidas por comandos do assistente pela interface. **Não é uma suíte autônoma de Playwright**, não contém testes de API e não afirma execução em CI.

## Falhas documentadas

| ID | Conta | Comportamento | Severidade | Prioridade sugerida |
|---|---|---|---|---|
| BUG-001 | problem_user | Seleção de preço crescente não se aplica | Média | Média |
| BUG-002 | problem_user | Nome da mochila abre detalhes da jaqueta | Alta | Alta |
| BUG-003 | problem_user | Remove no catálogo mantém a mochila no carrinho | Alta | Alta |

São falhas funcionais reproduzidas em **conta de treinamento**, documentadas como exercício. Não são apresentadas como incidentes de produção ou descobertas inéditas. A intenção de inserir defeitos não foi confirmada com os responsáveis pela aplicação. Não foram abertas issues no projeto da Sauce Labs.

Relatórios completos: [passos, impacto, comparação e evidências](bug-reports/bug-reports.md).

## Navegue pelo projeto

| Documento | Conteúdo |
|---|---|
| [Plano](test-plan/test-plan.md) | Seleção, escopo, critérios e riscos |
| [Casos](test-cases/test-cases.md) | 27 casos, dados, procedimentos, esperado e obtido |
| [Falhas](bug-reports/bug-reports.md) | Três relatórios reproduzíveis |
| [Execução](test-execution/execution-report.md) | Indicadores, sequência, exclusões e limites |
| [Evidências](evidence/README.md) | Capturas e registros textuais da interface |
| [Aprendizados](lessons-learned/learning-notes.md) | Conceitos, roteiro de reprodução e entrevista |
| [Publicação](PUBLISHING.md) | Preparação e passos manuais para GitHub |

## Evidência de execução

A confirmação abaixo foi capturada depois de finalizar o pedido fictício com standard_user. Ela comprova este estado, não todos os casos do projeto.

![Pedido fictício concluído](evidence/screenshots/CT-018-compra-concluida.jpg)

As capturas originais são JPEG, formato retornado pelo navegador. Os registros textuais complementam o que não cabe no viewport. [Índice de evidências](evidence/README.md).

## Aprendizados e próximos passos

Separar regra de negócio de suposição, controlar estado inicial, verificar correspondência entre telas e comunicar impacto sem inventar causa técnica. A entrada A/B/1 foi aceita; como não há especificação postal, ficou como pergunta de requisito, não bug confirmado.

Próximos passos: Bianca reproduzir os casos sozinha, registrar navegador/versão/sistema, esclarecer regras de formulários, ampliar dispositivos e acessibilidade, depois automatizar fluxos estáveis e manter os defeitos de treinamento identificados. Nenhuma dessas etapas futuras está marcada como concluída.

Este projeto registra uma sessão específica. O site pode mudar; reproduções futuras devem criar uma nova execução e preservar estes resultados.
