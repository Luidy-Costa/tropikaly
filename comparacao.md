# Comparação entre Sistemas

Abaixo, o quadro comparativo entre o sistema de produção analisado (Tropykaly) e o sistema didático visto anteriormente:

| Critério | Sistema Real (Tropykaly) | Sistema Didático |
| :--- | :--- | :--- |
| **Arquitetura** | Cliente-Servidor (desacoplada) | Monolítica / Simples |
| **Coesão** | Alta (módulos focados em seu domínio) | Baixa (lógica misturada) |
| **Acoplamento** | Moderado (comunicação via Controllers/APIs) | Alto (regras na interface) |
| **Organização** | Boa e padronizada | Confusa |
| **Flexibilidade**| Alta (fácil inserção de novos itens) | Baixa (engessado) |

## Principais Diferenças
A principal distinção reside na **separação de responsabilidades**. O sistema real demonstra flexibilidade para escalar: a adição de uma nova categoria de lanche não parece quebrar o layout, sugerindo que os dados (Model) estão bem isolados da apresentação (View). Por outro lado, o sistema didático apresentava alto acoplamento, onde qualquer alteração na interface corria o risco de afetar as regras de negócio do pedido.