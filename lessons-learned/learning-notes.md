# Aprendizados e apresentação em entrevista

## O que este trabalho exercitou

Um **caso de teste** descreve uma situação, dados e critério esperado. Uma **execução** é a tentativa real e seu resultado. Um caso pode ser executado várias vezes; repetir BUG-002 não transforma um defeito em dois.

**Oráculo** é a referência usada para decidir o que deveria acontecer. Neste projeto, a opção “preço crescente” exige uma ordem numérica e o nome clicado deve corresponder ao detalhe aberto. As credenciais vieram da própria tela. Não havia especificação dizendo quantos caracteres um código postal deveria ter; exigir cinco ou oito seria inventar uma regra.

**Partição de equivalência** agrupa entradas com comportamento semelhante: credenciais válidas, inválidas e vazias. **Limites** ajudam a testar transições: zero → um → dois itens, remoção para um e para zero, campo vazio → um caractere. Não foi realizada uma análise completa de comprimentos máximos porque eles não foram definidos.

**Transição de estados** é a passagem entre situações: deslogado → autenticado; catálogo → carrinho; checkout → confirmação. Conferir um produto ao longo dessas telas ajuda a encontrar perdas ou trocas de informação.

## Como reconhecer um bug

1. Defina o esperado usando uma referência verificável.
2. Estabeleça conta, dados e estado inicial.
3. Execute uma ação e observe o resultado.
4. Repita o caminho e verifique se o sintoma retorna.
5. Compare com outra conta quando isso esclarecer o alcance.
6. Registre o que foi observado; se faltar requisito, escreva uma dúvida, não uma conclusão.

Exemplo real: clicar no nome Backpack abriu Fleece Jacket. A identidade está errada independentemente de conhecer detalhes internos do código. Na conta padrão, o mesmo caminho abriu a mochila, fortalecendo a comparação. A reprodução ficou restrita à mesma sessão; ainda não prova ocorrência em todos os navegadores.

## Evidências úteis

A captura mostra o resultado final. Para um desenvolvedor reproduzir a sequência, acrescente conta, pré-condição, ação, esperado, obtido e registro textual. No BUG-003, a mochila visível no carrinho só ganha significado porque os passos registram dois cliques anteriores em Remove no catálogo.

Não editar imagens para “melhorar” uma falha. Não usar arquivo de exemplo como se fosse captura real. Neste pacote, os JPEGs são capturas efetivamente retornadas pelo navegador. Não há vídeo, telemetria de rede ou diagnóstico de código.

## Severidade e prioridade

**Severidade**: tamanho do impacto funcional. Ordenação quebrada recebeu média: comparar fica difícil, mas o catálogo pode ser consultado. Detalhe de outro produto recebeu alta porque compromete a seleção. **Prioridade**: urgência sugerida para resolver, considerando o negócio. Neste exercício é proposta, não uma decisão de um Product Owner.

Uma falha reproduzida em conta de demonstração não exige urgência real de produção. As classificações exercitam como tratar o mesmo sintoma em uma loja real, respeitando o alcance medido. Não houve falha crítica comprovada.

## Como apresentar para desenvolvimento

“Com problem_user, no catálogo, selecionei Price (low to high). A opção voltou a Name (A to Z) e os preços permaneceram começando por 29.99 e 9.99. Repeti a seleção com o mesmo resultado. Com standard_user, a ordenação ficou crescente. Os passos e registros estão no BUG-001. Sugiro severidade e prioridade médias. Não investiguei a causa no código.”

Essa comunicação oferece reprodução e alcance sem adivinhar a implementação.

## Como apresentar em entrevista

Modelo fiel ao estágio atual:

> Estou construindo meu portfólio de QA com um estudo de testes funcionais no SauceDemo. Usei assistência de IA para operar o navegador e organizar a documentação. O projeto registra 25 casos executados, 22 aprovados e três falhas reproduzidas em problem_user. Comparei esses fluxos com a conta padrão e documentei passos, impacto e evidências. Um exemplo é a mochila que abre os detalhes de uma jaqueta. Também separei dúvidas de requisito de defeitos: a aceitação de um código postal curto não foi classificada como bug sem regra definida. Agora estou reproduzindo os casos para ganhar autonomia.

Depois de reproduzir pessoalmente, atualizar a última frase e registrar uma nova execução. Não dizer “descobri vulnerabilidades”, “automatizei com Playwright” ou “validei todos os cenários”: este trabalho não comprova essas afirmações.

## Prática para Bianca — ainda não realizada

1. Baixar o pacote e ler CT-001, CT-006 e CT-022.
2. Reproduzir esses três casos sem copiar o resultado esperado para o obtido.
3. Anotar navegador/versão/sistema e data reais.
4. Reproduzir BUG-002 duas vezes e registrar uma captura própria.
5. Explicar em voz alta por que “clicou na mochila e abriu jaqueta” é mais preciso que “o site está errado”.

A execução independente ainda não foi avaliada; não há prova de domínio só por este pacote ter sido criado. Este projeto complementa estudos de API; não altera os projetos existentes.
