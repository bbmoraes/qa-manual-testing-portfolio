# Casos de teste e resultados

Sessão EX-001 — 21/10/2026, America/Sao_Paulo. Execução assistida por IA pela interface real do Chrome. Casos consolidados após exploração; não representam roteiro integral escrito antes das ações. Contas e dados estão no procedimento de cada caso.

| ID | Funcionalidade | Cenário | Resultado esperado | Resultado obtido | Status |
|---|---|---|---|---|---|
| CT-001 | Login | Credenciais públicas válidas | Products e catálogo | Products com seis produtos | Passed |
| CT-002 | Login | Senha inválida | Negar acesso com mensagem de credenciais | Epic sadface: Username and password do not match any user in this service | Passed |
| CT-003 | Login | Ambos os campos vazios | Exigir username | Epic sadface: Username is required | Passed |
| CT-004 | Login | Senha vazia | Exigir password | Epic sadface: Password is required | Passed |
| CT-005 | Login | Conta bloqueada | Negar acesso por bloqueio | Epic sadface: Sorry, this user has been locked out. | Passed |
| CT-006 | Catálogo | Preço crescente | Preços em ordem crescente | 7.99; 9.99; 15.99; 15.99; 29.99; 49.99 | Passed |
| CT-007 | Catálogo | Nome decrescente | Nomes de Z a A | Test.allTheThings; Onesie; Fleece Jacket; Bolt T-Shirt; Bike Light; Backpack | Passed |
| CT-008 | Detalhes | Abrir mochila pelo nome | Backpack e preço 29.99 | Backpack e preço 29.99 | Passed |
| CT-009 | Carrinho | Adicionar um produto nos detalhes | Um item e botão Remove | Cart, 1 items e Remove | Passed |
| CT-010 | Carrinho | Dois produtos distintos | Backpack 29.99 + Bike Light 9.99; QTY 1 cada | Dois itens, nomes e preços corretos; QTY 1 cada | Passed |
| CT-011 | Carrinho | Remover Bike Light | Somente mochila; contador 1 | Somente Backpack 29.99; contador 1 | Passed |
| CT-012 | Carrinho | Persistir após recarga | Manter mochila e quantidade 1 | Mochila e quantidade 1 mantidas | Passed |
| CT-013 | Checkout | Formulário vazio | Exigir First Name | Error: First Name is required | Passed |
| CT-014 | Checkout | Sobrenome vazio | Exigir Last Name | Error: Last Name is required | Passed |
| CT-015 | Checkout | Código postal vazio | Exigir Postal Code | Error: Postal Code is required | Passed |
| CT-016 | Checkout | Dados fictícios preenchidos | Avançar ao Overview | Overview com mochila | Passed |
| CT-017 | Checkout | Conferência aritmética | 29.99 + 2.40 = 32.39 | Subtotal 29.99; Tax 2.40; Total 32.39 | Passed |
| CT-018 | Checkout | Finalizar pedido fictício | Confirmação e carrinho vazio | Thank you for your order!; Cart, empty | Passed |
| CT-019 | Navegação | Voltar ao catálogo | Products e carrinho vazio | Products e Cart, empty | Passed |
| CT-020 | Sessão | Logout | Retornar ao formulário de login | Form Login com Username e Password | Passed |
| CT-021 | Catálogo | Ordenação em problem_user | Aplicar ordem crescente como na conta padrão | Não altera: A to Z permanece; preços começam por 29.99, 9.99 | Failed |
| CT-022 | Detalhes | Identidade em problem_user | Clicar Backpack deve abrir Backpack 29.99 | Abre Fleece Jacket 49.99 em duas tentativas | Failed |
| CT-023 | Carrinho | Remoção no catálogo em problem_user | Retirar mochila; contador vazio | Após dois cliques em Remove, contador 1; mochila também permanece no carrinho | Failed |
| CT-024 | Checkout | Cancelar resumo | Voltar ao catálogo mantendo item | Products com mochila e contador 1 | Passed |
| CT-025 | Carrinho | Remover último item no catálogo padrão | Carrinho vazio e botão Add to cart | Cart, empty e Add to cart; estado mantido após recarga | Passed |
| CT-026 | Pesquisa | Buscar produto por texto | Executar pesquisa se houver campo | Campo de pesquisa não localizado no catálogo examinado; ação não executada | Not Run |
| CT-027 | Carrinho | Alterar quantidade do mesmo produto | Executar alteração se houver controle | QTY exibida como texto 1; controle de edição não localizado; ação não executada | Not Run |

## Procedimentos e rastreabilidade

Senha pública das contas de demonstração: `secret_sauce`. Cada evidência textual é uma extração real da interface, não uma simulação. As capturas usam JPEG nativo do navegador; não foram renomeadas para PNG.

### CT-001 — Credenciais públicas válidas

Login deslogado; standard_user / secret_sauce. Preencher ambos e clicar Login.

Evidência: [registro real](../evidence/logs/auth.txt).

### CT-002 — Senha inválida

Deslogado; standard_user / senha_incorreta. Preencher ambos e clicar Login.

Evidência: [registro real](https://github.com/user-attachments/assets/c0e1e316-d52d-4560-be65-bd093a1b917b).

### CT-003 — Ambos os campos vazios

Deslogado. Limpar explicitamente os dois campos e clicar Login.

Evidência: [registro real](../evidence/logs/control.txt).

### CT-004 — Senha vazia

Deslogado. Preencher standard_user, limpar password e clicar Login.

Evidência: [registro real](../evidence/logs/auth.txt).

### CT-005 — Conta bloqueada

Deslogado. Entrar com locked_out_user / secret_sauce.

Evidência: [registro real](../evidence/logs/auth.txt).

### CT-006 — Preço crescente

standard_user autenticado. Selecionar Price (low to high) e conferir os seis preços.

Evidência: [registro real](../evidence/logs/catalog.txt).

### CT-007 — Nome decrescente

standard_user autenticado. Selecionar Name (Z to A) e comparar nomes.

Evidência: [registro real](../evidence/logs/catalog.txt).

### CT-008 — Abrir mochila pelo nome

standard_user no catálogo. Clicar no nome Sauce Labs Backpack.

Evidência: [registro real](../evidence/logs/catalog.txt).

### CT-009 — Adicionar um produto nos detalhes

standard_user nos detalhes da mochila; carrinho vazio. Clicar Add to cart.

Evidência: [registro real](../evidence/logs/cart.txt).

### CT-010 — Dois produtos distintos

Mochila adicionada. Back to products; abrir Bike Light pelo nome; Add to cart; abrir Cart.

Evidência: [registro real](../evidence/logs/cart.txt).

### CT-011 — Remover Bike Light

standard_user com dois itens no carrinho. Clicar Remove da Bike Light (segunda linha).

Evidência: [registro real](../evidence/logs/checkout1.txt).

### CT-012 — Persistir após recarga

Após CT-011, recarregar a página do carrinho e conferir item.

Evidência: [registro real](../evidence/logs/checkout1.txt).

### CT-013 — Formulário vazio

standard_user com mochila. Checkout; sem preencher dados, clicar Continue.

Evidência: [registro real](../evidence/logs/checkout1.txt).

### CT-014 — Sobrenome vazio

Na tela de dados, preencher apenas First Name=A; Continue.

Evidência: [registro real](../evidence/logs/checkout2.txt).

### CT-015 — Código postal vazio

First Name=A e Last Name=B; postal vazio. Clicar Continue.

Evidência: [registro real](../evidence/logs/checkout2.txt).

### CT-016 — Dados fictícios preenchidos

Preencher Pessoa / Teste / 12345 e clicar Continue.

Evidência: [registro real](../evidence/logs/checkout2.txt).

### CT-017 — Conferência aritmética

No Overview do CT-016, comparar item e somar valores exibidos. Não avalia conformidade tributária.

Evidência: [registro real](../evidence/logs/checkout2.txt).

### CT-018 — Finalizar pedido fictício

Overview com mochila. Clicar Finish. Nenhum pagamento real.

Evidência: [registro real](../evidence/logs/complete.txt).

### CT-019 — Voltar ao catálogo

Na confirmação, clicar Back Home.

Evidência: [registro real](../evidence/logs/complete.txt).

### CT-020 — Logout

Após CT-019, Open Menu → Logout. Não avalia invalidação de tokens no servidor.

Evidência: [registro real](../evidence/logs/complete.txt).

### CT-021 — Ordenação em problem_user

Login problem_user / secret_sauce, carrinho vazio. Selecionar Price (low to high); observar e repetir seleção. BUG-001.

Evidência: [registro real](../evidence/logs/problem2.txt).

### CT-022 — Identidade em problem_user

problem_user no catálogo. Clicar no nome Backpack; Back to products; repetir. BUG-002.

Evidência: [registro real](../evidence/logs/problem3.txt).

### CT-023 — Remoção no catálogo em problem_user

problem_user com carrinho vazio. No catálogo, Add to cart da Backpack; Remove; repetir; abrir carrinho. BUG-003.

Evidência: [registro real](../evidence/logs/problem4.txt).

### CT-024 — Cancelar resumo

standard_user com mochila. Checkout, A/B/1, Continue; no Overview clicar Cancel.

Evidência: [registro real](../evidence/logs/boundary.txt).

### CT-025 — Remover último item no catálogo padrão

standard_user com mochila persistida da conta anterior. Após login verificado, clicar Remove e recarregar.

Evidência: [registro real](../evidence/logs/standardcontrol.txt).

### CT-026 — Buscar produto por texto

Recurso não disponível na interface examinada. Não é classificado como defeito.

Evidência: [registro real](../evidence/logs/catalog.txt).

### CT-027 — Alterar quantidade do mesmo produto

Recurso não disponível na interface examinada. Não é classificado como defeito.

Evidência: [registro real](../evidence/logs/cart.txt).
