# Análise do Sistema (Tropykaly Pizzas e Lanches)

## 1. O que o sistema faz (Objetivo e Interação)
Basicamente, a plataforma é um e-commerce voltado para o *food service*. O fluxo do cliente é simples e direto: você entra na loja virtual, navega pelo cardápio (Pizzas, Lanches, Bebidas, Combos), customiza os itens que quer, joga no carrinho e finaliza o pedido preenchendo os dados para entrega.

## 2. Como ele parece estar estruturado (Arquitetura)
Pelo comportamento da aplicação no navegador, a arquitetura segue o modelo tradicional Cliente-Servidor Web, bem dividida:
- **Frontend (Apresentação):** A interface responsiva com a qual o usuário interage.
- **Backend (Aplicação/API):** O servidor que processa a lógica pesada (cálculo do total do carrinho, regras e taxas da área de entrega).
- **Banco de Dados (Persistência):** Onde ficam salvos os produtos, o histórico dos pedidos e os dados do restaurante.

Dá para notar uma separação clara entre as telas que o usuário vê e as engrenagens que processam os pedidos no fundo.

## 3. Design e Acoplamento
- **Coesão:** É alta. O sistema não tenta abraçar o mundo; ele foca exclusivamente em um único domínio: vender comida.
- **Acoplamento:** Parece ser de moderado a baixo. O catálogo de produtos e o motor do carrinho funcionam de um jeito bem modular, sem um travar o outro.

## 4. Justificativa da Modelagem (Parte 6)
Para o diagrama de classes, foquei em uma estrutura que reflete como os dados precisam se comportar em um sistema de delivery real:
- **Composição entre Pedido e ItemPedido:** Escolhi usar uma relação de composição porque um `ItemPedido` não faz sentido existir sozinho; ele pertence estritamente a um `Pedido` específico.
- **ItemPedido como Classe Intermediária:** Essa classe é vital para registrar o estado do produto no momento da compra (como preço unitário e quantidade), garantindo que, se o preço do `Produto` mudar no banco de dados amanhã, o histórico do pedido do cliente permaneça correto.
- **Organização por Categoria:** A relação entre `Categoria` e `Produto` permite que o cardápio seja expansível e fácil de filtrar, exatamente como vemos na interface da Tropykaly.

## 5. Reflexão Crítica (Parte 10)
Após realizar essa análise de engenharia reversa, cheguei a algumas conclusões sobre o processo:
1. **Modelagem sem código:** É perfeitamente possível (e muito comum) modelar um sistema apenas observando seu comportamento (análise de caixa-preta). Ao observar como os itens entram no carrinho e como as categorias se comportam, conseguimos deduzir as entidades e regras de negócio por trás da interface.
2. **Importância da Modelagem:** Ficou claro que a modelagem é o que sustenta o crescimento do software. Sem uma estrutura bem pensada (como o MVC e os padrões Singleton e Factory sugeridos), qualquer alteração simples pode gerar um efeito dominó de bugs, especialmente em sistemas reais que lidam com dinheiro e entregas.
3. **Real vs. Didático:** A grande lição é que o sistema real precisa ser resiliente. Enquanto o sistema didático costuma ignorar problemas de acoplamento para facilitar o ensino, o sistema em produção precisa de camadas bem definidas para garantir que o negócio não pare por falhas técnicas simples.