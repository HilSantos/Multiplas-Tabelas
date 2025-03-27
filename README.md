# Multiplas-Tabelas
Criação de tabelas usando MySql do ambiente PHP.

1. Liste todos os pedidos, incluindo o nome do cliente.
SELECT pedido_id, cliente_nome
FROM tb_pedidos
-------------------------------------------------------------------------------------------------------------------------------

2. Mostre todos os produtos vendidos, incluindo a quantidade total de cada.
SELECT produto_id, quantidade
FROM tb_itens_pedido
-------------------------------------------------------------------------------------------------------------------------------

3. Exiba os clientes que já realizaram um pedido.
SELECT cliente_nome, pedido_data
FROM tb_clientes
JOIN tb_pedidos
ON tb_pedidos.cliente_id = tb_clientes.cliente_id
-------------------------------------------------------------------------------------------------------------------------------

4. Mostre os clientes que ainda não fizeram pedidos.
SELECT cliente_nome, pedido_data
FROM tb_pedidos
JOIN tb_clientes
ON tb_clientes.cliente_id = tb_pedidos.pedido_data
WHERE pedido_data IS NULL
-------------------------------------------------------------------------------------------------------------------------------

5. Liste os pedidos que ainda não possuem pagamentos.
SELECT pedido_data, pagamento_valor
FROM tb_pedidos
JOIN tb_pagamentos
ON tb_pagamentos.pagamento_id = tb_pedidos.pedido_id
-------------------------------------------------------------------------------------------------------------------------------

6. Exiba o nome dos clientes e o total gasto em seus pedidos pagos.
SELECT cliente_nome, pagamento_valor
FROM tb_pagamentos
JOIN tb_clientes
ON tb_clientes.cliente_id = tb_pagamentos.pagamento_id
-------------------------------------------------------------------------------------------------------------------------------

7. Liste os pedidos e seus produtos correspondentes.
SELECT pedido_data, produto_nome
FROM tb_pedidos
JOIN tb_produtos
ON tb_produtos.produto_id = tb_pedidos.pedido_id
-------------------------------------------------------------------------------------------------------------------------------

8. Exiba os pedidos e a data do pagamento correspondente (se houver).
SELECT pedido_data, pagamento_data
FROM tb_pedidos
JOIN tb_pagamentos
ON tb_pagamentos.pagamento_id = tb_pedidos.pedido_id
-------------------------------------------------------------------------------------------------------------------------------

9. Exiba os clientes que compraram um determinado produto (por exemplo, "Notebook").
SELECT cliente_nome, produto_nome
FROM tb_clientes
JOIN tb_produtos
ON tb_produtos.produto_id = tb_clientes.cliente_id
-------------------------------------------------------------------------------------------------------------------------------

10. Mostre os clientes que já fizeram mais de um pedido.
SELECT cliente_nome, pedido_data
FROM tb_clientes
JOIN tb_pedidos
ON tb_pedidos.pedido_id = tb_clientes.cliente_id
GROUP BY cliente_nome
HAVING COUNT(pedido_data) > 1
------------------------------------------------------------------------------------------------------------------------------

11. Exiba os pedidos que contêm mais de um item.
SELECT pedido_data
FROM tb_pedidos
JOIN tb_itens_pedido
ON tb_itens_pedido.pedido_id = tb_pedidos.pedido_id
GROUP BY pedido_data
HAVING COUNT(item_id) > 1
-------------------------------------------------------------------------------------------------------------------------------
