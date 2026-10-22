# Índice de evidências

Capturas reais sem edição de conteúdo. Os nomes identificam os JPEGs originais do pacote ZIP entregue. Neste repositório, as imagens são anexos PNG no GitHub, obtidos por conversão dos JPEGs sem alterar seus pixels. Não há arquivos JPEG binários versionados nesta pasta; consulte também o [índice visual](screenshots/README.md). Cada imagem registra o viewport final, não uma gravação da sequência. Os textos em logs são saídas reais da leitura da interface; podem incluir elementos de navegação fora da área visível. Credenciais foram ocultadas automaticamente em algumas extrações. Nenhuma credencial pessoal foi usada nos testes.

| Captura | Relação |
|---|---|
| [CT-001-login-sucesso.jpg](https://github.com/user-attachments/assets/3183326f-bcae-41c5-8abd-d2dd8ef1ded0) | CT-001: catálogo após login válido. |
| [CT-002-login-invalido.jpg](https://github.com/user-attachments/assets/c0e1e316-d52d-4560-be65-bd093a1b917b) | CT-002: mensagem após senha inválida. |
| [CT-003-campos-vazios.jpg](https://github.com/user-attachments/assets/2163c618-07e0-4b34-a88f-3b75aa181cef) | CT-003: mensagem de username obrigatório. |
| [CT-010-carrinho-dois-produtos.jpg](https://github.com/user-attachments/assets/b19f73c5-c4e6-4dbf-b007-400926951eae) | CT-010: mochila e luz no carrinho. |
| [CT-015-cep-obrigatorio.jpg](https://github.com/user-attachments/assets/5b0056fb-879a-427c-8251-3a2003db92d9) | CT-015: código postal obrigatório. |
| [CT-017-resumo-compra.jpg](https://github.com/user-attachments/assets/bd4fe7a0-0027-42dd-a789-c55a6e56fc32) | CT-016/017: resumo e valores do pedido. |
| [CT-018-compra-concluida.jpg](https://github.com/user-attachments/assets/21ee4864-37d0-4e48-9f1a-19e7aff6c10e) | CT-018: confirmação de pedido fictício. |
| [BUG-001-ordenacao.jpg](https://github.com/user-attachments/assets/76104623-0b3d-47c0-b3ee-7e9e0a91cf38) | CT-021/BUG-001: estado final da ordenação não aplicada. |
| [BUG-002-produto-incorreto.jpg](https://github.com/user-attachments/assets/9a27fb30-ad1e-4214-bbf3-998301b6858b) | CT-022/BUG-002: jaqueta após clicar no nome da mochila. |
| [BUG-002-reproducao.jpg](https://github.com/user-attachments/assets/ca1d6fe2-f01e-4d41-b931-3aa009046443) | CT-022/BUG-002: segunda navegação com mesmo resultado. |
| [BUG-003-produto-permanece.jpg](https://github.com/user-attachments/assets/579df390-bedd-4f2d-a9b3-d4840d4d5645) | CT-023/BUG-003: mochila no carrinho após tentativas de remoção no catálogo. |

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

O pacote ZIP entregue contém SHA256SUMS.txt para conferir os arquivos originais. Esse manifesto não descreve as adaptações de links desta publicação; um hash não comprova sozinho quando ou como um teste foi executado.
