# Proposta de Arquitetura e Padrões de Projeto

## Organização em MVC
Para garantir manutenibilidade e escalabilidade, a aplicação deve seguir o padrão arquitetural MVC:
- **Model:** Classes que representam o domínio, como `Produto`, `Pedido` e `ItemPedido`, responsáveis pelas regras de negócio e validações de estado.
- **View:** Componentes de interface Web consumindo os dados.
- **Controller:** Orquestradores como `PedidoController` e `ProdutoController`, que interceptam as requisições HTTP, consultam os Models e devolvem a resposta para a View.

## Aplicação de Padrões de Projeto (Design Patterns)
1. **Factory Method:** Pode ser aplicado na criação de produtos complexos. Uma `ProdutoFactory` centralizaria a lógica de instanciar diferentes tipos de itens (ex: instanciar uma Pizza Meio a Meio exige regras diferentes de instanciar uma Bebida).
2. **Singleton:** Ideal para gerenciar recursos únicos e globais do escopo da requisição, como a conexão com o banco de dados ou o gerenciamento de estado do Carrinho de Compras ativo na sessão do usuário.