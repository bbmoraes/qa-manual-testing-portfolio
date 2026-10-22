# Índice de evidências

Capturas reais JPEG sem edição de conteúdo. Cada imagem registra o viewport final, não uma gravação da sequência. Os textos em logs são saídas reais da leitura da interface; podem incluir elementos de navegação fora da área visível. Credenciais foram ocultadas automaticamente em algumas extrações. Nenhuma credencial pessoal foi usada nos testes.

| Captura | Relação |
|---|---|
| [CT-001-login-sucesso.jpg](screenshots/CT-001-login-sucesso.jpg) | CT-001: catálogo após login válido. |
| [CT-002-login-invalido.jpg](screenshots/CT-002-login-invalido.jpg) | CT-002: mensagem após senha inválida. |
| [CT-003-campos-vazios.jpg](screenshots/CT-003-campos-vazios.jpg) | CT-003: mensagem de username obrigatório. |
| [CT-010-carrinho-dois-produtos.jpg](screenshots/CT-010-carrinho-dois-produtos.jpg) | CT-010: mochila e luz no carrinho. |
| [CT-015-cep-obrigatorio.jpg](screenshots/CT-015-cep-obrigatorio.jpg) | CT-015: código postal obrigatório. |
| [CT-017-resumo-compra.jpg](screenshots/CT-017-resumo-compra.jpg) | CT-016/017: resumo e valores do pedido. |
| [CT-018-compra-concluida.jpg](screenshots/CT-018-compra-concluida.jpg) | CT-018: confirmação de pedido fictício. |
| [BUG-001-ordenacao.jpg](screenshots/BUG-001-ordenacao.jpg) | CT-021/BUG-001: estado final da ordenação não aplicada. |
| [BUG-002-produto-incorreto.jpg](screenshots/BUG-002-produto-incorreto.jpg) | CT-022/BUG-002: jaqueta após clicar no nome da mochila. |
| [BUG-002-reproducao.jpg](screenshots/BUG-002-reproducao.jpg) | CT-022/BUG-002: segunda navegação com mesmo resultado. |
| [BUG-003-produto-permanece.jpg](screenshots/BUG-003-produto-permanece.jpg) | CT-023/BUG-003: mochila no carrinho após tentativas de remoção no catálogo. |

## Registros textuais

| Arquivo | Conteúdo |
|---|---|
| [auth.txt](logs/auth.txt) | Senha vazia, conta bloqueada e login válido. |
| [catalog.txt](logs/catalog.txt) | Duas ordenações na conta padrão e detalhes da mochila. |
| [cart.txt](logs/cart.txt) | Inclusão de um e dois produtos; conteúdo do carrinho. |
| [checkout1.txt](logs/checkout1.txt) | Remoção de Bike Light, recarga e First Name obrigatório. |
| [checkout2.txt](logs/checkout2.txt) | Last Name e Postal Code obrigatórios; avanço e totais. |
| [complete.txt](logs/complete.txt) | Confirmação, Back Home e logout. |
| [problem1.txt](logs/problem1.txt) | Login em problem_user e primeira seleção de preço. |
| [problem2.txt](logs/problem2.txt) | Segunda seleção e primeira abertura incorreta de detalhes. |
| [problem3.txt](logs/problem3.txt) | Seletor habilitado, segunda abertura incorreta e adição de mochila. |
| [problem4.txt](logs/problem4.txt) | Dois cliques Remove no catálogo e conferência do carrinho. |
| [control.txt](logs/control.txt) | Campos vazios repetidos; observação de troca de conta não conclusiva, excluída das conclusões. |
| [standardcontrol.txt](logs/standardcontrol.txt) | Login verificado; remoção da mochila no catálogo padrão e recarga. |
| [boundary.txt](logs/boundary.txt) | Entrada A/B/1 e cancelamento do resumo. |

Não há captura individual para todos os casos: os registros textuais são as evidências disponíveis para parte deles. A evidência CT-002 é visual; sua extração textual não foi arquivada separadamente. Os IDs das capturas se referem à tabela final de casos.

SHA256SUMS.txt na raiz permite conferir se os arquivos foram alterados desde o empacotamento; um hash não comprova sozinho quando ou como um teste foi executado.
