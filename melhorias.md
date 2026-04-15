# Problemas e Sugestões de Melhoria

## O que percebi de estranho (Inferência)
Como não temos acesso ao código-fonte, levantei algumas suspeitas testando e observando como a aplicação se comporta:
- **Lógica vazando para a View:** Quando a internet dá uma oscilada, o carrinho às vezes demora a atualizar os valores na tela. Isso levanta a suspeita de que a sincronização entre a interface e o banco de dados ainda tenha um leve nível de acoplamento.
- **Fragilidade no Checkout:** Se o sistema não estiver gerenciando bem os estados, o cliente pode acabar gerando problemas (como dados inconsistentes ou pedidos duplicados) caso fique voltando as páginas do navegador na hora de pagar.

## Como eu resolveria isso
Para deixar o sistema mais robusto e evitar dor de cabeça no futuro, sugiro as seguintes mudanças na arquitetura:
1. **Levar o MVC a sério:** Garantir que toda a matemática importante (cálculos do carrinho, taxas de entrega e validações) fique estritamente isolada nos *Models*, usando os *Controllers* apenas para orquestrar tudo de forma limpa.
2. **Controlar o Carrinho com Singleton:** Como o cliente só pode ter um carrinho ativo por acesso, usar o padrão *Singleton* garante que a aplicação não vai instanciar múltiplos carrinhos na mesma sessão, evitando conflitos na hora de fechar a conta.
3. **Usar Factory para produtos complexos:** Montar uma pizza meio a meio ou um hambúrguer cheio de adicionais exige muita regra de criação. Jogar isso num padrão *Factory* tira esse peso do construtor padrão, centraliza a criação desses objetos e deixa o código bem mais limpo.