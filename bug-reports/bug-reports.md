# Relatórios de falhas reproduzidas

EX-001 — 21/10/2026, America/Sao_Paulo. Três falhas funcionais observadas em `problem_user`, em aplicação de demonstração. São exercícios de documentação em ambiente de treinamento, não alegações de incidentes de produção ou descobertas inéditas. A existência de uma conta chamada `problem_user` sugere comportamento deliberadamente defeituoso; essa intenção não é necessária para comprovar o resultado observado. Não há requisito de produção fornecido nem validação dos responsáveis pelo produto.

Ambiente comum: SauceDemo, https://www.saucedemo.com/, Chrome conectado por extensão; versão do navegador, sistema operacional e build não verificados. Não usar o sistema operacional da usuária como se fosse uma medição desta sessão. Dados públicos de demonstração: `problem_user / secret_sauce`. Controle de comparação: `standard_user / secret_sauce`. URL do catálogo observada: https://www.saucedemo.com/inventory.html. Para detalhes e carrinho, navegar pelos controles abaixo; URLs dessas telas não foram registradas explicitamente.

## BUG-001 — Seleção de preço crescente não se aplica em problem_user

- **Caso:** CT-021; controle CT-006.
- **Pré-condições:** login como problem_user; catálogo padrão com seis produtos; carrinho vazio.
- **Resultado esperado:** selecionar `Price (low to high)` deve ordenar 7.99, 9.99, 15.99, 15.99, 29.99, 49.99, como observado com standard_user.
- **Resultado obtido:** permanece selecionado `Name (A to Z)`; a sequência continua 29.99, 9.99, 15.99, 49.99, 7.99, 15.99.
- **Severidade:** média — impede ordenar preços, mas permite examinar o catálogo.
- **Prioridade sugerida:** média — afeta descoberta e comparação de produtos; não é decisão de triagem de um time real.
- **Status:** reproduzido; duas seleções com mesmo resultado na mesma sessão, sem recarga entre elas.

### Passos para reproduzir

1. Acessar a tela de login; sair de eventual sessão anterior.
2. Preencher explicitamente problem_user e secret_sauce; clicar Login.
3. No catálogo, selecionar `Price (low to high)` em `Sort products`.
4. Observar opção selecionada e sequência dos seis preços.
5. Repetir a seleção e comparar o resultado.

Evidências: [primeira tentativa](../evidence/logs/problem1.txt), [segunda tentativa](../evidence/logs/problem2.txt), [controle padrão](../evidence/logs/catalog.txt). A leitura do DOM confirmou que o seletor e suas opções não estavam desabilitados ([registro](../evidence/logs/problem3.txt)). A captura isolada mostra o estado final; a ação e a comparação dependem dos passos e registros, não só da imagem.

![Estado após seleção](https://github.com/user-attachments/assets/76104623-0b3d-47c0-b3ee-7e9e0a91cf38)

## BUG-002 — Nome da mochila abre detalhes da jaqueta em problem_user

- **Caso:** CT-022; controle CT-008.
- **Pré-condições:** problem_user autenticado no catálogo; carrinho vazio.
- **Resultado esperado:** clicar no nome `Sauce Labs Backpack` deve mostrar a mochila e preço US$ 29,99, mantendo a identidade do produto selecionado.
- **Resultado obtido:** a página de detalhes mostra `Sauce Labs Fleece Jacket`, descrição de jaqueta e US$ 49,99.
- **Severidade:** alta — quebra a correspondência entre produto escolhido e detalhes apresentados; pode induzir escolha incorreta. Compra incorreta não foi executada nem comprovada.
- **Prioridade sugerida:** alta — compromete a confiança na seleção do produto.
- **Status:** reproduzido; duas navegações a partir do nome da mochila, na mesma sessão.

### Passos para reproduzir

1. Entrar com problem_user / secret_sauce.
2. No catálogo, clicar no **nome** `Sauce Labs Backpack` (não na imagem).
3. Observar nome, descrição e preço no detalhe.
4. Clicar `Back to products`.
5. Clicar novamente no nome da mochila e observar a jaqueta.

Evidências: [primeira navegação](../evidence/logs/problem2.txt), [reprodução](../evidence/logs/problem3.txt), [mesma seleção na conta padrão](../evidence/logs/catalog.txt).

![Jaqueta após clicar na mochila](https://github.com/user-attachments/assets/9a27fb30-ad1e-4214-bbf3-998301b6858b)

![Reprodução](https://github.com/user-attachments/assets/ca1d6fe2-f01e-4d41-b931-3aa009046443)

## BUG-003 — Remove da mochila no catálogo não retira o item em problem_user

- **Caso:** CT-023; controle CT-025.
- **Pré-condições:** problem_user autenticado; carrinho inicialmente vazio; catálogo em ordem padrão.
- **Resultado esperado:** após adicionar a mochila e clicar Remove no catálogo, ela deve sair do carrinho, o contador ficar vazio e o botão voltar a Add to cart.
- **Resultado obtido:** após dois cliques em Remove, o botão e contador 1 permanecem; abrindo o carrinho, a mochila continua listada com quantidade 1.
- **Severidade:** alta — impede retirar um item por uma ação principal de edição da seleção. Não se afirma ausência de qualquer alternativa, pois a remoção pela tela de carrinho em problem_user não foi testada.
- **Prioridade sugerida:** alta — afeta controle da seleção antes de finalizar a compra.
- **Status:** reproduzido; dois cliques com observação intermediária, na mesma sessão.

### Passos para reproduzir

1. Entrar como problem_user com carrinho vazio.
2. No catálogo, clicar Add to cart da primeira linha, `Sauce Labs Backpack`.
3. Conferir contador 1 e botão Remove na mochila.
4. Clicar Remove e observar que item/contador permanecem.
5. Repetir Remove e conferir novamente.
6. Abrir o carrinho; conferir Backpack, quantidade 1 e US$ 29,99.

Evidências: [adição](../evidence/logs/problem3.txt), [duas tentativas e verificação no carrinho](../evidence/logs/problem4.txt), [remoção da mesma mochila no catálogo padrão após novo login verificado](../evidence/logs/standardcontrol.txt).

![Mochila permanece no carrinho](https://github.com/user-attachments/assets/579df390-bedd-4f2d-a9b3-d4840d4d5645)

## Observações que não viraram bugs

- Não há campo de busca nem controle de quantidade nas telas examinadas. Ausência de requisito impede classificá-los como defeitos.
- O checkout aceitou A / B / 1 e abriu Overview. É uma observação de limite inferior não vazio; um código postal com um caractere pode justificar discutir regras de validação. Não há país ou formato especificado, portanto não foi aberto bug nem declarado que seja um endereço válido.
- Uma captura estática comprova o estado final, mas não toda a sequência. Os registros de interface e os passos complementam as imagens. Não foi gravado vídeo.
- Causas no código não foram investigadas. Não há correção implementada nem reteste pós-correção.
