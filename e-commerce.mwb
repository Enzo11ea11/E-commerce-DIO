create database ecommerce;
use ecommerce;

create table cliente(
		idCliente int auto_increment primary key,
        Fnome varchar(10),
        Minit varchar(3),
        Lnome varchar(20),
        CPF char(11) not null,
        Endereço varchar(30),
        constraint unique_cpf_client unique (CPF)
);
desc cliente;

create table produto(
	idProduto int auto_increment primary key,
    Pnome varchar(10) not null,
    categoria enum ('Eletrônico', 'Vestimenta', 'Brinquedo', 'Alimentos', 'Móveis', 'Infantil') not null,
    avaliação float,
    tamanho varchar(10)
);

create table pagamento(
	idClient int,
    idPagamento int,
    tipoPagamento enum('Boleto', 'Cartão', 'Dois cartões', 'PIX'),
    limitAvaliado float,
    primary key(idCliente, idPagamento)
);


create table pedido(
	idPedido int auto_increment primary key,
    idPedidoCliente int,
    orderStatus enum('Cancelado', 'Confirmado', 'Em processamento') default 'Em processamento',
    pedidoDesc varchar(255),
    valorPedido float default 10,
    paymentCash bool default false,
    constraint fk_orders_client foreign key (idPedidoCliente) references client(idCliente)
);
desc pedido;

create table estoque(
	idProdEstoque int auto_increment primary key,
    edenreçoEstoque varchar(225),
    quantidadeEstoque int default 0
);


create table fornecedor(
	idFornecedor int auto_increment primary key,
    nomeSocial varchar(255) not null,
    CNPJ char(15) not null,
    contato char(11) not null,
    constraint PK_fornecedor unique (CNPJ)
);

create table vendedor(
	idVendedor int auto_increment primary key,
    nomeSocial varchar(255) not null,
    nomeAlt varchar(255),
    CNPJ char(15),
    CPF char(11),
    localização varchar(255),
    contato char(11) not null,
    constraint pk_cnpj_vendedor unique (CNPJ),
    constraint pk_cpf_vendedor unique (CPF)
);
create table produtoVendedor(
	idPvendedor int,
    idProduto int,
    quantidadeProd int default 1,
    primary key (idPvendedor, idProduto),
    constraint pk_produto_vendedor foreign key (idPseller) references vendedor(idVendedor),
    constraint pk_produto_produto foreign key (idProduct) references produto(idProduto)
);
create table produtoPedido(
	idPPproduto int,
    idPPpedido int,
    ppQuantidade int default 1,
    ppStatus enum('Disponível', 'Sem estoque') default 'Disponível',
    primary key (idPPproduto, idPPpedido),
    constraint fk_produtopedidor_vendedor foreign key (idPPproduto) references produto(idProduto),
    constraint fk_produtopedidor_produto foreign key (idPPpedido) references pedido(idPedido)
);
create table localArmazenamento(
	idLproduto int,
    idLestoque int,
    endereço varchar(255) not null,
    primary key (idLproduto, idLestoque),
    constraint fk_estoque_endereço_produto foreign key (idLproduto) references produto(idProduto),
    constraint fk_estoque_endereço_estoque foreign key (idLestoque) references produtoPedido(idProdEstoque)
);

show tables;

create table produtoFornecedor(
	idPsfornecedor int,
    idPsproduto int,
    quantidadeEstoque int not null,
    primary key (idPsfornecedo, idPsproduto),
    constraint fk_produto_fornecedor_fornecedor foreign key (idPsfornecedor) references fornecedor(idFornecedor),
    constraint fk_produto_fornecedor_produto foreign key (idPsproduto) references produyo(idProduto)
);

desc produtoFornecedor;
