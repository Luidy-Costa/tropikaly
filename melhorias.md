# Problemas Identificados e Melhorias Propostas

## Problemas Identificados (via Inferência de Comportamento)
[cite_start]Como não temos acesso ao código[cite: 9], inferimos os seguintes pontos com base no comportamento da aplicação:
- **Possível Acoplamento de Lógica na View:** Em momentos de oscilação de rede, o carrinho pode apresentar pequenos atrasos na atualização de estado, o que pode indicar que a sincronização entre interface e banco de dados pode estar levemente acoplada.
- **Limitações de Arquitetura no Checkout:** Se o sistema não utilizar um gerenciamento de estado robusto, o fluxo de finalização do pedido pode gerar inconsistências de dados caso o cliente retroceda páginas durante o pagamento.

## Melhorias Propostas
Para sanar os problemas e garantir uma base sólida de código, propõem-se as seguintes melhorias arquiteturais:
1. **Adoção Estrita do Padrão MVC:** Garantir que o cálculo total de pedidos, taxas de entrega e regras de validação fiquem isolados nos *Models*, orquestrados de forma limpa pelos *Controllers*.
2. **Implementação de um Singleton para Sessão:** Centralizar o gerenciamento do Carrinho de Compras em um *Singleton*, garantindo que apenas uma única instância do carrinho exista durante a sessão do cliente, evitando conflitos de itens.
3. **Uso de Factory para Entidades Complexas:** Como há muita variação entre os produtos (ex: montar meia-pizza, lanches com adicionais extras), utilizar o padrão *Factory* para centralizar a lógica de instanciação desses diferentes objetos, aliviando a carga do construtor padrão.