# Arquitetura e Padrões de Projeto

## Organização em MVC
Para o código não virar uma bagunça conforme o sistema cresce, a base da aplicação precisa seguir firme com o padrão MVC:
- **Model:** As classes que realmente importam para o negócio, como `Produto`, `Pedido` e `ItemPedido`. É aqui que moram as regras e validações de estado.
- **View:** A interface web, focada apenas em renderizar os dados para o cliente.
- **Controller:** Os maestros do sistema (como `PedidoController` e `ProdutoController`). Eles pegam o que o usuário clicou na tela, conversam com o Model e devolvem a resposta certinha pra View.

## Design Patterns Recomendados
Além do MVC, alguns padrões de projeto fariam muita diferença na organização do código:
1. **Factory Method:** Perfeito para lidar com a criação de produtos que têm muitas variações. Uma `ProdutoFactory` centraliza a lógica, porque instanciar uma pizza com duas metades e borda recheada exige regras muito diferentes de simplesmente instanciar uma lata de refrigerante.
2. **Singleton:** Essencial para cuidar de recursos globais que precisam ser únicos durante a requisição, como a própria conexão com o banco de dados ou o gerenciamento do Carrinho de Compras ativo na sessão do cliente.