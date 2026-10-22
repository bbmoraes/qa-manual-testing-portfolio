# Relatório de execução — EX-001

**Data:** 21/10/2026, America/Sao_Paulo. Horários por caso não coletados; não foram reconstruídos. Aplicação pública: https://www.saucedemo.com/. Ambiente: Chrome; versão, sistema e build não verificados.

## Indicadores

| Indicador | Resultado |
|---|---:|
| Casos registrados | 27 |
| Executados (Passed + Failed) | 25 |
| Passed | 22 |
| Failed | 3 |
| Blocked | 0 |
| Not Run | 2 |
| Falhas distintas reproduzidas | 3 |
| Aprovação entre executados | 88% (22/25) |
| Execução do conjunto registrado | 92,59% (25/27) |

Fonte: [results.json](results.json), uma linha por caso; [metrics.json](metrics.json). Tentativas de reprodução não são contadas como casos adicionais. Esses percentuais descrevem este conjunto de cenários; não medem a qualidade geral do produto ou cobertura total de requisitos. As contas não devem ser agregadas para inferir qualidade de produção.

## Resultados por frente

- standard_user, validações de acesso e locked_out_user: 22 casos Passed, incluindo pedido fictício com confirmação. A passagem de CT-025 também serve de comparação com BUG-003.
- problem_user: 3 casos Failed, cada qual vinculado a um relatório. A adição de mochila foi preparação para CT-023, não um quarto caso aprovado.
- Pesquisa e alteração de quantidade: 2 Not Run, por ausência dos controles na interface examinada. Não são Blocked por falha da aplicação.
- Entrada A/B/1: observação exploratória documentada à parte. A navegação e o cancelamento são CT-024; não se contou validação postal como aprovação de regra desconhecida.

## Sequência e controles da sessão

1. Reconhecimento e primeiros ensaios de login. Um clique inicial sem limpeza explícita abriu o catálogo. A entrada efetiva não foi comprovada nessa tentativa; ela foi descartada das métricas, sem atribuir bug.
2. Login com ambos os campos explicitamente preenchidos/limpos; mensagens negativas, bloqueio e conta válida.
3. Ordenação, detalhes e carrinho com standard_user. Dois itens, remoção da Bike Light e recarga do carrinho.
4. Validações de campos e compra fictícia da mochila: subtotal US$ 29,99, taxa US$ 2,40, total US$ 32,39. A soma foi conferida; não se validou uma regra fiscal externa.
5. Logout e problem_user: ordenação e identidade do detalhe, ambas repetidas; adição de mochila seguida de duas tentativas de remoção no catálogo e inspeção no carrinho.
6. Volta à conta padrão. Uma observação logo após troca de conta não demonstrou estado estável e foi preservada em control.txt, mas descartada como conclusão. Novo logout, preenchimento de standard_user verificado visualmente, login e remoção da mochila resultaram em carrinho vazio, inclusive após recarga (standardcontrol.txt). Não se atribuiu causa técnica à observação descartada.
7. Exploração A/B/1, cancelamento do Overview e retorno ao catálogo (boundary.txt).
8. Limpeza final/logout foram solicitados ao navegador, mas a chamada completa terminou sem retorno ao verificar o GitHub. Não se afirma a limpeza final como verificada e não se conta nova execução. O último estado documentado de teste é catálogo com um item após Cancel. Há remoção completa comprovada anteriormente em CT-025.

Os IDs são agrupados por funcionalidade, não por ordem temporal estrita. CT-025 foi executado antes de CT-024. A duplicação de tentativas ajuda a reproduzir falhas, mas não constitui reteste de uma correção.

## Evidências e limites

Capturas JPEG originais em [screenshots](../evidence/screenshots/) e extrações textuais em [logs](../evidence/logs/). Consulte o [índice](../evidence/README.md) para relacionar arquivos a casos. A resolução varia conforme o tamanho capturado pelo navegador, sem simular dispositivos.

Não executado: outros navegadores, dispositivos móveis, acessibilidade completa, segurança, carga, API, PDF do pedido, Dynamic Catalog, links externos, checkout vazio, formatos postais internacionais e limites máximos de texto. Nenhum desses recursos é implicitamente aprovado. Os botões/links testados são aqueles descritos nos procedimentos; não há cobertura de todos os links do site.

## Parecer

O fluxo positivo com a conta padrão funcionou nos cenários executados. Três falhas reproduzidas em problem_user foram registradas para exercício técnico de QA. Sem requisitos formais ou mandato de homologação, este relatório não autoriza uma liberação de produção. Próximo ciclo sugerido: esclarecer regras de formulários, testar novas contas e ampliar cobertura antes de automatizar cenários estáveis.

Execução e documentação realizadas com assistência de IA operando o navegador. Bianca deve reproduzir os casos e revisar a documentação antes de apresentar domínio independente em entrevistas.
