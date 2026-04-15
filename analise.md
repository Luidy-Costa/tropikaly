# Análise do Sistema Real (Tropykaly Pizzas e Lanches)

## Parte 1 – Objetivo e Interação
O sistema atua como uma plataforma de e-commerce focada em *food service*, permitindo que clientes realizem pedidos online. 
O fluxo de interação do usuário consiste em: acessar a vitrine digital, navegar pelas categorias (Pizzas, Lanches, Bebidas, Combos), selecionar itens customizáveis, adicionar ao carrinho e finalizar o *checkout* com informações de entrega.

## Parte 2 – Arquitetura
A arquitetura inferida é Cliente-Servidor (Web), fortemente dividida em camadas tradicionais:
- **Frontend (Apresentação):** Interface responsiva processada no navegador do cliente.
- **Backend (Aplicação/API):** Servidor que processa as regras de negócio (cálculo de carrinho, validação de área de entrega).
- **Banco de Dados (Persistência):** Armazenamento de produtos, pedidos e dados da loja.
Existe uma clara separação de responsabilidades entre a camada de apresentação e a lógica de processamento dos pedidos.

## Parte 3 – Design
- **Coesão:** Alta. O sistema é focado em um único domínio de negócio (venda de alimentos).
- **Acoplamento:** Aparenta ser moderado/baixo, já que o catálogo de produtos e o motor do carrinho funcionam de forma modular.