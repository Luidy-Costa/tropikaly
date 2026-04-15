# Comparação entre os Sistemas

Aqui está um comparativo direto entre o sistema em produção que analisei (Tropykaly) e o projeto didático que vimos antes:

| Critério | Tropykaly (Sistema Real) | Sistema Didático |
| :--- | :--- | :--- |
| **Arquitetura** | Cliente-Servidor (bem separada) | Monolítica / Mais simples |
| **Coesão** | Alta (módulos focados no próprio domínio) | Baixa (lógica misturada) |
| **Acoplamento** | Moderado (comunicação limpa via APIs/Controllers) | Alto (regras jogadas direto na interface) |
| **Organização** | Padronizada | Confusa |
| **Flexibilidade**| Alta (fácil adicionar novidades) | Baixa (código engessado) |

## Onde está a maior diferença?
A principal diferença é, sem dúvida, a **separação de responsabilidades**. O sistema real mostra que aguenta escalar: se o restaurante adicionar uma categoria nova de lanches amanhã, isso não vai quebrar o layout. Isso prova que os dados (Model) estão bem isolados da tela (View). Já o sistema didático era super acoplado, onde qualquer mexidinha no visual corria o risco de bugar a regra de negócio e quebrar o fechamento do pedido.