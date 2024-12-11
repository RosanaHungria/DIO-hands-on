# DIO-hands-on
Escopo:
Modelo de banco de dados EER para um sistema de e-commerce com suporte a múltiplos fornecedores, vendas por terceiros, rastreamento de entregas e gerenciamento de pagamentos.
Este projeto foi desenvolvido utilizando o MySQL Workbench.
Recursos Incluídos:
Diagrama EER completo com as entidades:
Cliente
Produto
Fornecedor
Estoque
Pedido
ItemPedido
Entrega
Forma de Pagamento
Terceiro-Vendedor

Relacionamentos:
•	Cliente → Pedido (1:N)
•	Pedido → ItemPedido (1:N)
•	Produto → ItemPedido (1:N)
•	Fornecedor → Estoque (1:N)
•	Produto → Estoque (1:N)
•	FormaPagamento → Cliente (N:N)
•	Cliente → FormaPagamento (1:N)
•	Pedido → Entrega (1:1)

Suporte a: Clientes do tipo Pessoa Física (PF) e Jurídica (PJ).
Relacionamento de um cliente com múltiplas formas de pagamento. 
Rastreio de entregas com status e código de acompanhamento. 
Relacionamento entre produtos, fornecedores e pedidos.

Regras:
1.	Cliente PJ e PF – Uma conta pode ser PJ ou PF, mas não ambas
Para modelar incluí um campo para diferenciar o tipo de cliente:
campo tipo_cliente: coluna tipo_cliente com valores possíveis “PJ” ou “PF” usando ENUM. Isso impede que ambos os tipos sejam usados simultaneamente.
2.	Pagamento – Pode ter mais de uma forma de pagamento
Para suportar múltiplas formas de pagamento, adicionei uma tabela separada para representar as formas de pagamento associadas ao cliente ou ao pedido:
O cliente pode cadastrar múltiplas formas de pagamento.
         3. Entrega – Status e Código de Rastreio
A entrega será vinculada ao pedido e terá seus próprios atributos para rastrear o progresso:
status: Para representar o progresso da entrega.
codigo_rastreio: Código fornecido pela transportadora para rastreamento.
