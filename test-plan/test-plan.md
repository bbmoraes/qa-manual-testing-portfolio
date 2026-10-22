# Plano de testes — SauceDemo

Plano inicial: login → catálogo → detalhes → carrinho → checkout → logout. Execução em 21/10/2026 (America/Sao_Paulo), pela interface pública de https://www.saucedemo.com/.

## Objetivo e seleção
Verificar o fluxo funcional de uma loja fictícia, com casos positivos, negativos e limites de entrada. SauceDemo foi escolhido por oferecer contas públicas de demonstração e um fluxo integrado de compra sem pagamento real. Não foi necessário migrar para Automation Exercise ou The Internet; essas alternativas não foram testadas.

## Escopo
Login válido/inválido, obrigatoriedade, usuário bloqueado, ordenação, navegação, inclusão/remoção de itens, persistência por recarga, formulários e conclusão fictícia. Exploração adicional de problem_user, separada da conta de referência standard_user.

## Abordagem
Caixa-preta (comportamento externo), partição de equivalência (válido, inválido, vazio), limites observáveis (zero/um/dois itens e vazio/um caractere), transição de estados (catálogo/carrinho/checkout) e exploração guiada por risco. Não se afirma cobertura completa ou análise de valores-limite de comprimentos máximos: não há especificação fornecida.

## Oráculos e critérios
Credenciais: publicadas na própria tela de login. Ordenação: opção escolhida deve corresponder à sequência visível. Carrinho: produto, preço e quantidade devem permanecer coerentes entre telas. Obrigatoriedade: baseada nas mensagens da própria aplicação. Checkout: totais devem coincidir aritmeticamente com o resumo; sem afirmar regra fiscal externa. Na ausência de requisito formal, comportamento suspeito é hipótese ou melhoria, salvo inconsistência funcional reproduzida e comparada com a conta de referência.

## Ambiente e dados
Chrome conectado pela extensão de navegador. Versão do Chrome e sistema operacional da sessão não verificados; não inferidos do computador da usuária. Viewport não alterado. Build da aplicação não exposto. Contas públicas standard_user, locked_out_user e problem_user; senha de demonstração secret_sauce. Dados de checkout totalmente fictícios.

## Preparação, riscos e saída
Controlar campos explicitamente para evitar preenchimento automático. Isolar carrinho por remoção e confirmar estado vazio. Repetir possíveis defeitos, registrar conta e comparar com standard_user. Sem ataques, carga, dados pessoais, compras reais ou contato com terceiros. Encerrar com todos os casos planejados classificados e limitações documentadas. Alteração de quantidade e pesquisa dependem de controles disponíveis; ausência de recurso não é automaticamente bug.
